## Virtualização Conceitos

A ideia da virtualização nasceu com a publicação do artigo *Time sharing processing in large fast computers*, na Conferência Internacional de Processamento de Informação, realizada em Nova York em 1959. Escrito pelo cientista da computação Christopher Strachey, o artigo tratou do uso da multiprogramação em tempo compartilhado.

Baseado no trabalho inicial de Strachey, o MIT desenvolveu o padrão Compatible Time Sharing System (CTSS). Com base na evolução do padrão CTSS, a IBM introduziu o conceito de multiprocessamento nos mainframes, o que permitiu que várias CPUs trabalhassem como uma só, antecipando o conceito de virtualização.

Utilizando uma maquina virtual de processo inicialmente, onde esta nada mais é que uma aplicação que executa sobre um sistema operacional A e emula o comportamento de um sistema operacional B. Essa técnica permite que binários de um processador sejam interpretados e substituídos por código equivalente de outro processador. Além de emular o sistema operacional é possível emular processadores.

As desvantagens dessa técnica, maquina virtual de processo, são basicamente duas: pior desempenho e desperdício de capacidades do hardware físico.

Para resolver as desvantagens das maquinas virtuais de processo, surgiram os monitores de máquinas virtuais (Virtual Monitor Machine - VMM). Também conhecidos como hipervisores (hypervisors), são implementados como uma camada de software entre o hardware e o sistema operacional, oferecendo uma máquina virtual para o Sistema Operacional (SO).

Desta forma exploram de forma mais eficiente os dispositivos de E/S e o desempenho tende a ser melhor pois não executam processos em modo usuário evitando chaveamento de contexto.

---

## Virtualização Tipos

* **Virtualização de servidores:** a mais comum e fácil de ser justificada. Diferente da época dos mainframes, a virtualização dos servidores agora acontece em servidores x86.
* **Virtualização de desktops:** trata da configuração dos desktops dos usuários finais em uma infraestrutura centralizada virtual. Isso significa que as aplicações de desktop também passam a executar em um datacenter, sob a forma de máquinas virtuais. Este é o conceito de Virtual Desktop Infrastructure (VDI), que permite a montagem dinâmica de desktops, oferecendo maior confiabilidade e otimização do uso de espaço em disco.
* **Virtualização do armazenamento (storage):** a ideia é introduzir um componente (appliance) que permite que as diversas unidades heterogêneas de armazenamento (discos físicos) sejam vistas como um conjunto homogêneo de recursos de armazenamento.
* **Virtualização das aplicações:** trata do conceito de execução do programa por completo, em um repositório central, permitindo a configuração centralizada do aplicativo, o que melhora seu gerenciamento, além de permitir que a configuração ou reconfiguração seja feita em um único lugar.
* **Virtualização de redes:** arquitetura que proporciona um ambiente de rede separado para cada grupo ou organização. Estes ambientes lógicos são criados sobre uma única infraestrutura compartilhada de rede. Cada rede lógica fornece ao grupo de usuários correspondente com plenos serviços de rede, semelhantes aos utilizados por uma rede tradicional não virtualizada.

---

## Virtualização Categorias

* **Nível do hardware:** a camada de virtualização é posta diretamente sobre a máquina física e a apresenta às camadas superiores como hardware abstrato, similar ao original. Esse é o caso da maioria dos hipervisores (VMware ESX, Xen e Hyper-V).
* **Nível do sistema operacional:** mecanismo que permite a criação de partições lógicas em uma plataforma, de maneira que cada partição seja vista como uma máquina isolada, compartilhando o mesmo sistema operacional. A camada de virtualização está inserida entre o sistema operacional e as aplicações. Exemplos: Jails, OpenVZ, Solaris Zones, Containers, Linux-VServer, Parallels Virtuozzo, SandBox, KVM e VirtualBox.
* **Nível da linguagem de programação:** a camada de virtualização é um programa de aplicação do sistema operacional da plataforma. Define uma máquina abstrata sobre a qual executa uma aplicação desenvolvida em uma aplicação de alto nível. A máquina virtual Java (JVM) é o exemplo mais marcante.

---

## Virtualização Cenários

### Consolidação de Servidores:
* Comum encontrarmos o emprego da filosofia "um servidor por serviço";
* Internet Data Centers (IDC) mostram que somente cerca de 15% da capacidade dos servidores é utilizada, estando os 85% restantes ociosos;
* Conceito de TI verde (green computing), pois permite economia significativa de energia e espaço físico.
* Permite que várias máquinas virtuais, cada uma responsável por um serviço, executem sobre uma única máquina física.

### Melhorar a continuidade dos negócios:
* Possibilitar a continuidade dos negócios a um custo adequado, utilizando recursos já incorporados nos produtos de virtualização, como a alta disponibilidade (High Availability - HA) e a recuperação de desastres (Disaster Recovery - DR).

### Criar um novo ambiente de testes e desenvolvimento de software:
* Flexibilizar e portar máquinas virtuais tornam interessante seu uso em ambientes desktops, possibilitando por exemplo o desenvolvimento de produtos de softwares destinados a vários sistemas operacionais, sem a necessidade de uma plataforma física para desenvolver e testar cada um deles. Nesse caso, as máquinas virtuais em desktops podem ser usadas para a definição de ambientes experimentais completos, sem interferir no sistema operacional original da máquina.

### Proteger e gerenciar os desktops da empresa:
* Permite que cada usuário estabeleça uma sessão de trabalho dentro de um sistema centralizado, a partir de um cliente fino (thin client) ou de outro software cliente. A diferença desse tipo de virtualização para soluções do tipo "Terminal Services" é que cada usuário pode empregar um sistema operacional diferente totalmente isolado dos demais usuários. Com isto, o gerenciamento e a proteção ficam mais simples já que o sistema centralizado possui as imagens das maquinas virtuais. (Exemplo: kasmweb)

### Hospedar aplicações legadas:
* A virtualização é uma ferramenta muito útil para hospedar e executar sistemas legados. Como uma máquina virtual é um ambiente que inclui um sistema operacional, bibliotecas e aplicações de forma totalmente independente e isolada de outra máquina virtual, é possível manter versões de antigos sistemas operacionais e bibliotecas exigidas por sistemas legados. Sistema legado é termo utilizado para sistemas computacionais antigos que ainda fornecem serviços essenciais a uma organização.

### Datacenter mais dinâmico:
* Datacenter dinâmico utiliza os benefícios da virtualização para criar uma infraestrutura mais ágil, combinada com novos recursos de gerenciamento que permitem mover máquinas virtuais sem causar impacto sobre as atividades dos usuários. O conceito de datacenter dinâmico permite provisionar os recursos de forma imediata mediante a demanda.

---

## Mais sobre Virtualização Tipos

* **A virtualização completa** realiza toda a abstração do sistema físico, com o objetivo de fornecer ao sistema operacional hóspede uma réplica do hardware virtualizado pelo hospedeiro. Este tipo dispensa a necessidade de modificar o SO convidado, que trabalha desconhecendo que há virtualização.
  * *Desvantagem:* é o desempenho, pois o hipervisor verifica a execução de todas as instruções privilegiadas ou sensíveis feitas pelo sistema operacional convidado, e as substitui por ações equivalentes controladas.
* **A paravirtualização** requer a modificação do SO convidado. O sistema operacional visitante é modificado e passa a ter conhecimento que está rodando sobre a VMM. O hóspede modificado, então, não executa instruções privilegiadas diretamente, mas recorre ao hypervisor quando necessitar delas.
  * *Desvantagem:* é a necessidade de modificação do sistema operacional hospedado ou convidado, o que pressupõe acesso ao código-fonte.
* **A virtualização completa assistida por hardware** elimina a conversão binária e interrompe diretamente o hardware usando a tecnologia de virtualização integrada nos processadores X86 desde 2005 (Intel VT-x e AMD-V). As instruções do SO convidado podem permitir que um contexto virtual execute instruções privilegiadas diretamente no processador, mesmo que seja virtualizado.
  * *Detalhe:* Os hipervisores que suportam esta tecnologia podem funcionar no Anel -1 e os sistemas operacionais hóspedes podem aceder à CPU no Anel 0, como fariam normalmente se estivessem a ser executados numa máquina física. Isto permite virtualizar S.O. hóspedes sem nenhuma modificação.

---

## Virtualização Fornecedores e Licenciamento

* **Vmware:** VMware ESXi e VMware vSphere.
* **Microsoft:** Hyper-V, System Center Virtual Machine Manager (SCVMM).
* **Citrix:** Xen Server, Citrix Essentials for Hyper-V e Citrix Essentials for Xen Server.

Processadores com vários núcleos empregando virtualização aumentam a probabilidade do licenciamento de software utilizado estar inadequado. A maior parte dos softwares para servidor ainda está licenciada por soquete (CPU).

Tratando-se de licenciamento multicore, é preciso considerar dois aspectos novos: a quantidade de núcleos e a virtualização. A política de licenciamento entre fabricantes diferentes não é a mesma. A VMware, assim como a Citrix (XenServer), adotou o licenciamento por soquete. Já a Microsoft considera cada máquina virtual como um servidor físico com o mesmo número de soquetes do servidor real. Alguns fabricantes ainda contabilizam os núcleos da CPU, levando em consideração o desempenho de cada linha de processador (IBM e Oracle).

---

## Virtualização Limitações

* **Aplicativos de carga excessiva:** aplicativos de carga excessiva, incluindo SGBDs, podem ser um fator limitante. Considere que sempre existe uma perda de desempenho com a introdução de um HYPERVISOR. Se uma aplicação ou um sistema gerenciador de banco de dados já demanda parte dos recursos do servidor, qual a razão de virtualizá-lo?
* **Gerenciamento do licenciamento:** o licenciamento pode ser fator limitante. Deve ser observado a regra de cada aplicação (EULA - Acordo de licença de usuário). Em uma determinada situação de carga, o licenciamento é válido, em outro, que utiliza uma outra configuração de hardware, pode não ser.
* **Falta de profissional especializado:** ainda existem poucos profissionais experientes que dominem a técnica e as opções comerciais disponíveis. Este aspecto deve ser considerado quando da escolha do software de VIRTUALIZAÇÃO.

---

## Virtualização Desempenho e Benchmarks

Como a virtualização consiste basicamente em inserir uma camada de software adicional em um sistema computacional, a questão sobre quanto isso afeta o desempenho final é imediata. Estudos feitos pela VMware e pela XenSource apontam para uma queda de desempenho, em geral entre 2% e 10%, com algumas situações impondo perdas maiores.

Para a consolidação de uma forma padronizada e isenta de avaliação, um comitê específico (SPEC Virtualization Comitee) desenvolveu benchmarks para a virtualização, que pode ser encontrado em SPEC VIRT_SC® 2013 e em SPECvirt Datacenter 2021. O benchmark SPEC-virt Datacenter 2021 difere do benchmark SPEC VIRT_SC® 2013 pois o SPEC VIRT_SC mede o desempenho de um único host e fornece informações relevantes em nível de host. No entanto, a maioria dos data centers atuais utiliza clusters para garantir confiabilidade, disponibilidade, facilidade de manutenção e segurança.

**ALGUEM FALOU PROXMOX?**

Proxmox Virtual Environment (VE) é uma plataforma de virtualização de código aberto, baseada em Debian Linux, que permite gerenciar máquinas virtuais (KVM) e contêineres (LXC) em uma única interface web.

Gerencia servidores, armazenamento e redes virtualizadas. É gratuito (open-source), possui alta disponibilidade (clusters), backups integrados e é uma alternativa robusta ao Vmware. Ideal para qualquer empresa que busca virtualização com custo zero de licença. Mas lembre-se, é opensource mas não faz milagres, a mesma robustez de hardware que você iria investir em um server com VMWARE, deve ser aplicada em um server com PROXMOX.

Para continuar evoluindo, estes recursos podem ser muito úteis:
* Livros como "Proxmox VE in Practice" e "Proxmox VE for Absolute Beginners" oferecem roteiros estruturados.
* Plataformas como a NDG oferecem laboratórios interativos oficiais, cobrindo tópicos desde a instalação até clustering avançado.
* Ao se sentir confortável, explore a API do Proxmox com Terraform e Ansible para provisionar laboratórios inteiros com um único comando.

---

## Atividade

No VirtualBox providenciar a instalação do PROXMOX e na sequencia inicializar um container LXC Ubuntu server (somente texto). O PROMOX exige configuração mínima (avaliação/testes) de hardware.

* **Mínimo:** 2 vCPUs (Suporte Intel VT-x ou AMD-V), 2GB RAM (Só p/ PROXMOX), 10GB Disco (Só PROXMOX) e 1 Placa Rede.
* **Aconselhável:** 2 vCPUs+ (Suporte Intel VT-x ou AMD-V), 4GB+ RAM (Só p/ PROXMOX), 20GB+ Disco (Só PROXMOX) e 1 Placa Rede+.