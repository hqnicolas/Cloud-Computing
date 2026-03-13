---

#  Guia de Implementação: Cluster GlusterFS e Configuração de Rede

Este guia orienta a configuração de uma matriz de armazenamento em cluster redundante (Trusted Storage Pool) usando GlusterFS e a configuração de rede de servidores Linux.

##  Entendendo o GlusterFS

**GlusterFS** é um sistema de arquivos de armazenamento conectado à rede que permite agrupar recursos de várias máquinas. Ele trata múltiplos dispositivos de armazenamento distribuídos entre vários computadores como uma unidade única e poderosa.

**Objetivos desta prática:**
Criar uma *Trusted Storage Pool* que proporcionará funcionalidades semelhantes a uma configuração RAID espelhada pela rede. Cada servidor independente conterá sua própria cópia dos dados, permitindo que as aplicações acessem qualquer cópia e distribuindo a carga de leitura.

---

##  Fase 1: Preparação e Configuração de Rede

Antes de iniciar o GlusterFS, as máquinas virtuais precisam estar clonadas, com IPs fixos configurados e comunicando-se entre si.

### 1. Checklist Inicial

* [ ] Clonar as máquinas virtuais necessárias.
* [ ] Configurar os IPs fixos (veja as opções abaixo).
* [ ] Verificar se as máquinas possuem IP e se comunicam (teste com `ping`).

### 2. Configuração de Rede (Escolha a Opção A ou B)

#### Opção A: Usando o Netplan (Padrão no Ubuntu)

Para evitar que o *cloud-init* desabilite o Netplan automaticamente, crie/edite o arquivo abaixo:

```bash
sudo nano /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg

```

Adicione o seguinte conteúdo:

```yaml
network: {config: disabled}

```

Em seguida, edite o arquivo de configuração do Netplan:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml

```

Deixe-o com a seguinte estrutura (atenção à indentação):

```yaml
network:
    version: 2
    ethernets:
        eno1:
            addresses:
            - 192.168.10.30/24
            nameservers:
                addresses:
                - 208.67.220.220
                - 208.67.222.222
                - 8.8.8.8
            routes:
            -   metric: 100
                to: default
                via: 192.168.10.1

```

Aplique as configurações:

```bash
sudo netplan generate
sudo netplan apply

```

>  **Dica:** [Tutorial Oficial do Netplan](https://netplan.readthedocs.io/en/stable/netplan-tutorial/)

#### Opção B: Usando o ifupdown (Alternativa Simplificada)

Caso prefira não usar o Netplan, substitua-o pelo `ifupdown`:

```bash
sudo apt install ifupdown
sudo apt purge network-manager netplan.io
sudo rm -rf /etc/netplan/*.yml

```

Edite o arquivo de interfaces:

```bash
sudo nano /etc/network/interfaces

```

Adicione a configuração (ajuste `enp0s3` e `enp0s8` conforme suas placas de rede):

```text
auto lo
iface lo inet loopback

auto enp0s3
iface enp0s3 inet dhcp

auto enp0s8
iface enp0s8 inet static
address 192.168.36.1
netmask 255.255.255.0

```

---

## 🚀 Fase 2: Configuração do GlusterFS

### Identificação das Máquinas

A arquitetura do cluster será dividida da seguinte forma:

* **gluster0**: Servidor
* **gluster1**: Servidor
* **gluster2**: Cliente

### 1. Resolução de Nomes

Em **todas as 3 máquinas**, edite o arquivo hosts:

```bash
sudo nano /etc/hosts

```

Adicione as linhas abaixo (substitua pelos IPs reais que você configurou na Fase 1):

```text
127.0.0.1       localhost
192.168.X.X     gluster0.satc.net.br gluster0
192.168.X.X     gluster1.satc.net.br gluster1
192.168.X.X     gluster2.satc.net.br gluster2

```

### 2. Instalação do GlusterFS (Nos 3 Servidores)

Adicione o repositório em todas as máquinas e atualize:

```bash
sudo add-apt-repository ppa:gluster/glusterfs-7
sudo apt update

```

### 3. Configuração dos Servidores (`gluster0` e `gluster1`)

Instale o pacote do servidor e inicie o serviço apenas no **gluster0** e **gluster1**:

```bash
sudo apt install glusterfs-server
sudo systemctl start glusterd.service
sudo systemctl enable glusterd.service
sudo systemctl status glusterd.service

```

No **gluster0**, registre o `gluster1` como parte do pool de armazenamento (não é necessário rodar no gluster1 também):

```bash
sudo gluster peer probe gluster1

```

*Se for bem-sucedido, retornará: `peer probe: success`.*

Verifique o status da comunicação:

```bash
sudo gluster peer status

```

### 4. Criando e Iniciando o Volume

Ainda em um dos servidores, crie um volume replicado (2 cópias):

```bash
sudo gluster volume create volume1 replica 2 gluster0.satc.net.br:/gluster-storage gluster1.satc.net.br:/gluster-storage force

```

Inicie o volume:

```bash
sudo gluster volume start volume1

```

Verifique se o volume está online:

```bash
sudo gluster volume status

```

### 5. Configuração do Cliente (`gluster2`)

No cliente, instale o pacote correspondente, crie a pasta e monte a unidade:

```bash
sudo apt install glusterfs-client
sudo mkdir /storage-pool
sudo mount -t glusterfs gluster0.satc.net.br:/volume1 /storage-pool
df -h

```

---

## 📊 Fase 3: Testes e Monitoramento

Testando a gravação de arquivos a partir do cliente (`gluster2`):

```bash
cd /storage-pool
sudo touch file_{0..9}.test
ls -l /storage-pool

```

Comandos úteis para obter informações e debugar seu cluster:

```bash
sudo gluster volume info
sudo gluster peer status

```

Para realizar um **perfil de volume** (análise de desempenho de cada nó):

```bash
# Iniciar o perfil
sudo gluster volume profile volume1 start

# Obter as informações reunidas após algum tempo
sudo gluster volume profile volume1 info

```

---

##  O que deve ser entregue

Para comprovar a realização deste laboratório, você deve apresentar:

1. **Evidências de realização do trabalho** (prints ou logs das etapas concluídas com sucesso).
2. **Imagem das partições montadas** (saída do comando `df -h` no cliente).
3. **Arquivos sendo gravados** (saída provando que os arquivos criados no cliente replicaram nos servidores).
