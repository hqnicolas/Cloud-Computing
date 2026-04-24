## DHCP e VLAN na Nuvem: Conceitos e Aplicações Práticas

Explorando como DHCP e VLAN funcionam tanto em redes tradicionais quanto na infraestrutura virtualizada da Amazon Web Services.

---

## Revisão: DHCP e VLAN
Vamos revisar os conceitos fundamentais de DHCP e VLAN que servem como base essencial para compreender como esses protocolos se adaptam ao ambiente de nuvem.

### O que é DHCP?
O **Dynamic Host Configuration Protocol (DHCP)** é um protocolo de rede que automatiza a atribuição de endereços IP e outras configurações essenciais para dispositivos em uma rede TCP/IP.

* **Objetivo Principal:** Eliminar a necessidade de configuração manual de parâmetros de rede.
* **Comunicação:** Acontece através de mensagens **broadcast**, permitindo que dispositivos solicitem e obtenham configurações automaticamente.
* **Parâmetros Configuráveis:**
    * Endereço IP (IPv4/IPv6)
    * Máscara de sub-rede
    * Gateway padrão
    * Servidores DNS

### Como funciona o DHCP? (Processo de 4 Etapas)
1.  **DHCP Discover:** O cliente envia um broadcast na rede solicitando um endereço IP disponível.
2.  **DHCP Offer:** O servidor responde oferecendo um IP disponível junto com outras configurações (DNS, gateway, máscara).
3.  **DHCP Request:** O cliente aceita a oferta e solicita formalmente o uso do endereço IP proposto.
4.  **DHCP ACK:** O servidor confirma a atribuição e o cliente utiliza o IP por um tempo determinado (**lease**).

<img width="1118" height="468" alt="image" src="https://github.com/user-attachments/assets/73a77fb2-40dc-41b6-8b08-8e219bb1e32a" />

---

## O que é VLAN?
Uma **Virtual LAN (VLAN)** é uma tecnologia que permite a segmentação lógica de uma rede física em múltiplas redes virtuais isoladas, mesmo utilizando a mesma infraestrutura de hardware.

* **Controle de Broadcast:** Limita o domínio de broadcast, melhorando a performance.
* **Segurança Aprimorada:** Isola o tráfego entre diferentes grupos de usuários.
* **Flexibilidade:** Cada VLAN funciona como uma rede independente.

### O Desafio Técnico: VLANs e DHCP
A integração entre essas tecnologias apresenta um obstáculo:
1.  **DHCP usa broadcast:** Depende dessas mensagens para a comunicação inicial.
2.  **VLANs isolam broadcasts:** Por design, broadcasts não atravessam diferentes VLANs.
3.  **Problema:** Se o servidor e o cliente estiverem em VLANs diferentes, o cliente não recebe o IP.
4.  **Soluções:** Uso de **DHCP Relay Agents (IP Helper)** ou servidores DHCP dedicados em cada VLAN.

<img width="873" height="425" alt="image" src="https://github.com/user-attachments/assets/2e910f75-3344-41b6-92c2-e8435f8cc637" />


---

## DHCP e VLAN na Amazon Web Services (AWS)

### AWS VPC e DHCP
Na AWS, o **Virtual Private Cloud (VPC)** representa sua rede virtual isolada. Diferente do ambiente on-premises, o DHCP na AWS é **completamente gerenciado** pelo provedor.

* **Automação:** Instâncias EC2 obtêm IPs automaticamente através do serviço nativo.
* **DHCP Option Sets:** Permitem personalizar configurações como DNS, domínio e servidores NTP para todas as instâncias dentro de uma VPC.

### DHCP Option Sets
* **Configurações Centralizadas:** Conjunto de parâmetros aplicados automaticamente.
* **Personalização Limitada:** Apenas **um** DHCP Option Set pode ser associado a cada VPC por vez.
* **Aplicação Automática:** Novas instâncias herdam as configurações durante a inicialização.

### Funcionamento do DHCP na AWS
1.  **Solicitação:** Instâncias EC2 solicitam IP ao servidor gerenciado durante o boot.
2.  **Atribuição:** IPs são atribuídos dentro do range CIDR definido para a subnet.
3.  **DNS Padrão:** O DNS configurado é o **AmazonProvidedDNS (169.254.169.253)**.
4.  **Customização:** Alterações são feitas via DHCP Option Sets personalizados.

<img width="1271" height="804" alt="image" src="https://github.com/user-attachments/assets/09111bdb-6113-4f4a-a22f-567b72375fc8" />


---

## VLANs na AWS: Elas existem?
A resposta é complexa. A AWS **não suporta VLANs tradicionais 802.1Q** dentro do ambiente VPC pelas seguintes razões:
* VPCs utilizam isolamento em **Nível L3** (Camada de rede), não L2 (Enlace).
* A virtualização abstrai a camada física.
* Tags VLAN não são transportadas na infraestrutura VPC.

**Onde as VLANs existem na AWS?**
No **AWS Direct Connect**, que utiliza VLANs 802.1Q para conexões físicas dedicadas entre data centers on-premises e a nuvem, permitindo múltiplas interfaces virtuais (VIFs) isoladas.

### Alternativas para Segmentação
Como as VLANs tradicionais não funcionam na VPC, a segmentação é implementada via:
* **Subnets:** Pública, Privada e Database.
* **Tabelas de Roteamento.**
* **Segurança:** Security Groups e Network ACLs (NACLs).

---

## Exemplos Práticos na AWS

### Criando um DHCP Option Set Personalizado
1.  **Definir Parâmetros:** Configurar domínio (ex: `empresa.local`) e DNS internos.
2.  **Criar Option Set:** Via console ou CLI.
3.  **Associar à VPC:** Substituir as configurações padrão.
4.  **Validar:** Usar o Amazon Route 53 Resolver para resolução privada.

<img width="635" height="713" alt="image" src="https://github.com/user-attachments/assets/9cd550b4-eefe-454d-b394-3d5a1e1e113c" />


> **Exemplo de comando CLI:**
> `aws ec2 create-dhcp-options --dhcp-configurations Key=domain-name,Values=empresa.local Key=domain-name-servers,Values=10.0.0.10,10.0.0.11`

### Simulação de VLANs via Subnets
* **Subnet Pública:** Web servers com acesso à internet via Internet Gateway.
* **Subnet Privada:** Servidores de aplicação sem acesso direto.
* **Subnet Database:** Máximo isolamento para bancos de dados.

---

## Conclusão
Compreender a adaptação de conceitos clássicos como DHCP e VLAN para o ambiente de nuvem é fundamental para arquitetar redes seguras e eficientes. A AWS prioriza a escalabilidade e a abstração, substituindo protocolos L2 tradicionais por serviços gerenciados e segmentação em nível de camada 3.
