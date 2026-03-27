# Guia de Configuração: Redes e GlusterFS no Ubuntu

Este documento detalha o processo de configuração de rede estática via Netplan e a implementação de um sistema de arquivos distribuído utilizando **GlusterFS**.

---

## 1. Configuração de Rede (Netplan)

Antes de configurar o cluster, é essencial que as máquinas tenham IPs estáticos e não sofram alterações automáticas pelo Cloud-Init.

### Passo 1: Desabilitar configuração automática
Crie o arquivo para impedir que o Cloud-Init sobrescreva as configurações de rede:
```bash
sudo nano /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg
```
Adicione o seguinte conteúdo:
```yaml
network: {config: disabled}
```

### Passo 2: Configurar IP Estático
Edite o arquivo do Netplan (o nome pode variar, como `50-cloud-init.yaml` ou `01-netcfg.yaml`):
```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

**Exemplo de configuração:**
```yaml
network:
    version: 2
    ethernets:
        eno1: # Verifique o nome da sua interface com 'ip a'
            addresses:
                - 192.168.10.30/24
            nameservers:
                addresses:
                    - 8.8.8.8
                    - 1.1.1.1
            routes:
                - to: default
                  via: 192.168.10.1
```

### Passo 3: Aplicar as alterações
```bash
sudo netplan generate
sudo netplan apply
```

---

## 2. Preparação do Ambiente GlusterFS

O **GlusterFS** permite agrupar o armazenamento de várias máquinas em uma unidade única (**Trusted Storage Pool**), funcionando de forma similar a um RAID via rede.



### Identificação das Máquinas
| Hostname | Função |
| :--- | :--- |
| **gluster0** | Servidor de Armazenamento |
| **gluster1** | Servidor de Armazenamento |
| **gluster2** | Cliente |

### Mapeamento de Hosts
Em **todas** as máquinas, edite o arquivo `/etc/hosts`:
```bash
sudo nano /etc/hosts
```
Adicione os IPs correspondentes:
```text
127.0.0.1       localhost
IP_DA_MAQUINA_0 gluster0.satc.net.br gluster0
IP_DA_MAQUINA_1 gluster1.satc.net.br gluster1
IP_DA_MAQUINA_2 gluster2.satc.net.br gluster2
```

---

## 3. Instalação e Configuração do Cluster

### Passo 1: Adicionar Repositório (Executar nos 3 nós)
```bash
sudo add-apt-repository ppa:gluster/glusterfs-7
sudo apt update
```

### Passo 2: Instalar Servidor (Apenas gluster0 e gluster1)
```bash
sudo apt install glusterfs-server
sudo systemctl start glusterd.service
sudo systemctl enable glusterd.service
```

### Passo 3: Criar o Pool de Armazenamento
No **gluster0**, execute o comando para confiar no **gluster1**:
```bash
sudo gluster peer probe gluster1
```
*Deverá retornar: `peer probe: success`.*

Verifique o status da comunicação:
```bash
sudo gluster peer status
```

### Passo 4: Criar o Volume Replicado
Vamos criar um volume chamado `volume1` que espelha os dados entre os dois servidores:
```bash
sudo gluster volume create volume1 replica 2 gluster0.satc.net.br:/gluster-storage gluster1.satc.net.br:/gluster-storage force
```

Inicie o volume:
```bash
sudo gluster volume start volume1
```

---

## 4. Configuração do Cliente (gluster2)

No nó cliente, instale o suporte ao Gluster e monte o volume remoto:

```bash
# Instalação
sudo apt install glusterfs-client

# Criar ponto de montagem
sudo mkdir /storage-pool

# Montar o volume
sudo mount -t glusterfs gluster0.satc.net.br:/volume1 /storage-pool
```

### Teste de Funcionamento
Crie arquivos no cliente e verifique se eles aparecem nos servidores:
```bash
cd /storage-pool
sudo touch file_{0..9}.test
ls /gluster-storage # Executar nos servidores para validar
```

---

## 5. Comandos de Manutenção e Monitoramento

* **Informações do Volume:** `sudo gluster volume info`
* **Status do Peer:** `sudo gluster peer status`
* **Perfil de Desempenho:**
    ```bash
    sudo gluster volume profile volume1 start
    sudo gluster volume profile volume1 info
    ```

---

## Bônus: Alternativa ao Netplan (ifupdown)
Caso prefira o método clássico de configuração de rede:

1.  **Instalar e Remover:**
    ```bash
    sudo apt install ifupdown
    sudo apt purge network-manager netplan.io
    sudo rm -rf /etc/netplan/*.yml
    ```
2.  **Configurar `/etc/network/interfaces`:**
    ```text
    auto enp0s8
    iface enp0s8 inet static
        address 192.168.36.1
        netmask 255.255.255.0
    ```

---