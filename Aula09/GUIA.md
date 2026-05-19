# Guia de Monitoramento de Infraestrutura de TI com SNMP

##  Links Úteis e Referências

### Apresentação e Conceitos

* **Apresentação Principal:** [Como realizar o monitoramento de infraestrutura de TI - Maxinst](https://maxinst.com.br/como-realizar-o-monitoramento-de-infraestrutura-de-ti/)

### Comandos e Configurações de MIBs

* [Habilitando SNMP no Linux - OpServices](https://kb.opservices.com.br/knowledge-base/habilitando-snmp-linux-2/)
* [Linux SNMP OIDs para Estatísticas de CPU, Memória e Disco - DebianAdmin](http://www.debianadmin.com/linux-snmp-oids-for-cpumemory-and-disk-statistics.html)
* [Monitoring by SNMP - OpServices](https://kb.opservices.com.br/knowledge-base/monitoring-by-snmp/)
* [OIDView (Consulta de OIDs)](https://www.oidview.com/)
* [Monitorando uso de banda com SNMP, Shell Script e External Commands no Zabbix](https://stato.blog.br/wordpress/monitorando-uso-de-banda-com-snmp-shell-script-e-external-commands-zabbix/)
* [Passo a passo: Identificar parâmetro do SNMP](http://andredeo.blogspot.com/2008/06/passo-passo-identificar-parmetro-do.html)
* [Trabalhando com bibliotecas de MIBs para monitoramentos SNMP no Ubuntu/Debian](https://medium.com/@bernardolankheet/trabalhando-com-bibliotecas-de-mibs-para-monitoramentos-snmp-no-ubuntu-debian-c753d89481d8)

### Ferramenta de Teste de Carga (Stress)

* **stress-ng:** [Estressando CPU, Memória RAM e Disco Rígido no Linux com stress-ng](https://www.edivaldobrito.com.br/estressando-cpu-memoria-ram-e-disco-rigido-no-linux-com-stress-ng/)

---

## Instalação e Configuração Manual (Ubuntu Mini)

> **Credenciais Padrão do Ambiente:**
> * **Usuário:** `satc`
> * **Senha:** `satc`
> 
> 

Siga o passo a passo abaixo executando os comandos como root:

```bash
# Acessar como root
sudo su

# Atualizar a lista de pacotes
apt-get update 

# Instalar o daemon do SNMP
apt-get install snmpd*

# Instalar o tradutor de OIDs para nomes amigáveis
apt-get install snmp-mibs-downloader

```

### Configuração dos Arquivos

1. Edite o arquivo `/etc/snmp/snmp.conf`:
* Comente a linha `mibs :` adicionando uma `#` no início.
* Adicione a linha `mibs +ALL` logo abaixo.
* Salve e saia (`:x` ou `:wq`).


2. Edite o arquivo `/etc/snmp/snmpd.conf`:
* Habilite a linha de comunidade pública removendo o comentário: `rocommunity public`.
* Altere o endereço de escuta do agente para permitir conexões externas:
* **De:** `agentAddress udp:127.0.0.1:161`
* **Para:** `agentAddress udp:161`




3. Baixe as MIBs complementares para correção de erros:

```bash
# Baixar MIB do IANA
wget http://www.iana.org/assignments/ianaippmmetricsregistry-mib/ianaippmmetricsregistry-mib -O /var/lib/snmp/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB

# Baixar correções de MIBs do IETF
wget http://pastebin.com/raw.php?i=p3QyuXzZ -O /usr/share/snmp/mibs/ietf/SNMPv2-PDU
wget http://pastebin.com/raw.php?i=gG7j8nyk -O /usr/share/snmp/mibs/ietf/IPATM-IPMC-MIB

```

4. Reinicie e valide o serviço:

```bash
# Reiniciar o serviço do SNMP
/etc/init.d/snmpd restart

# Verificar o status do serviço
/etc/init.d/snmpd status

# Realizar um teste local para observar as MIBs
snmpwalk -v 1 -c public localhost

```

---

## Guia Rápido de Instalação e Resolução de Problemas (Scripts)

Caso prefira uma abordagem direta via terminal utilizando comandos modernos (`systemctl`), utilize o roteiro abaixo:

### 1. Instalação Básica

```bash
sudo apt update
sudo apt install -y snmpd snmp snmp-mibs-downloader

```

### 2. Configurar snmp.conf

```bash
echo "mibs +ALL" | sudo tee /etc/snmp/snmp.conf

```

### 3. Configurar snmpd.conf (Habilitar Comunidade)

```bash
sudo sed -i 's/^#rocommunity public/rocommunity public/' /etc/snmp/snmpd.conf

```

### 4. Reiniciar o Serviço

```bash
sudo systemctl restart snmpd

```

### 5. Teste de Funcionamento Inicial

```bash
snmpwalk -v 1 -c public localhost | head -20

```

### 6. Correção de Erros de MIBs (Se necessário)

Se o comando anterior retornar erros de parsing de MIBs, execute as correções abaixo com os repositórios oficiais atualizados:

```bash
# Baixar MIB IANA corrigida
sudo wget -O /var/lib/snmp/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB https://www.iana.org/assignments/ianaippmmetricsregistry-mib/ianaippmmetricsregistry-mib

# Atualizar MIBs do Net-SNMP do repositório oficial
sudo rm -f /usr/share/snmp/mibs/ietf/SNMPv2-PDU
sudo wget -O /usr/share/snmp/mibs/ietf/SNMPv2-PDU https://raw.githubusercontent.com/net-snmp/net-snmp/master/mibs/SNMPv2-PDU

sudo wget -O /usr/share/snmp/mibs/ietf/IPATM-IPMC-MIB https://raw.githubusercontent.com/net-snmp/net-snmp/master/mibs/IPATM-IPMC-MIB

# Limpar o cache de MIBs antigo
sudo rm -f ~/.snmp/mibcache/*

# Reiniciar o serviço para aplicar as alterações
sudo systemctl restart snmpd

```

### 7. Explorando Métricas de Carga (`UCD-SNMP-MIB::laLoad`)

Comandos para interagir e inspecionar os índices de Load Average (Carga do Sistema):

```bash
# Traduzir o nome amigável para a numeração OID correspondente
snmptranslate -On UCD-SNMP-MIB::laLoad

# Listar todas as entradas da árvore laLoad
snmpwalk -v 1 -c public localhost UCD-SNMP-MIB::laLoad

# Capturar especificamente o Load Average de 1 minuto (.1)
snmpget -v 1 -c public localhost UCD-SNMP-MIB::laLoad.1

# Exibir os dados estruturados em formato de tabela
snmptable -v 1 -c public localhost UCD-SNMP-MIB::laTable

```