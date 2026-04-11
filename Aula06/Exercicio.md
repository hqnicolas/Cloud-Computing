Aqui está o conteúdo formatado em Markdown para facilitar a leitura e organização:

# Simulado de Infraestrutura e Redes de Data Center

---

### Questão 1
**É fundamental que a Computer Room disponha de sistemas de combate e detecção de incêndios, por abrigar equipamentos de alto custo, necessários e críticos para o funcionamento de um Data Center. Diante disto, é correto afirmar que:**

- ( ) A norma **NFPA 75**, que trata de proteção contra fogo para equipamentos de TI, especifica o uso de materiais resistentes ao fogo de forma a separar a área que abriga esses equipamentos de outras áreas dentro de um edifício, com resistência mínima ao fogo de, pelo menos, uma hora.
- ( ) Os sistemas de detecção de incêndio fazem uso de sensores de fumaça, calor ou fogo. Os sensores de fogo podem operar por ionização, fotoelétrico ou dual. Cada tipo de sensor deve ser estrategicamente posicionado na *Computer Room*, tais como em racks, teto, paredes, etc.
- ( ) Após a detecção de fogo na *Computer Room*, o sistema de combate a incêndios deve ser acionado automaticamente, fazendo a supressão do fogo da sala com o uso de gases inertes, tais como o **FM200, CO2**, etc.
- ( ) Para retardar a propagação do fogo, é recomendado o uso de cabos de telecomunicações do tipo **CMG**, que apresentam a melhor proteção contra queima, atendendo requisitos de normas como a UL-1685.

---

### Questão 2
**Considerado o mais crítico em um Data Center, o sistema de distribuição elétrica deve alimentar continuamente os equipamentos mais importantes da TI. Para isso, se faz necessário o uso de sistemas auxiliares de alimentação, agregados aos componentes de distribuição convencional. Fazem parte dos sistemas auxiliares de distribuição elétrica:**

- ( ) No-breaks e chaves ATS.
- ( ) Unidades UPS e grupo motor-gerador.
- ( ) Unidades PDU e transformadores.
- ( ) Sistema de aterramento e sala de baterias.

---

### Questão 3
**Um Datacenter possui um sistema elétrico com as seguintes características:**
* Redundância **N+1** no sistema UPS;
* Alimentado por uma única concessionária por um único caminho de entrada;
* Grupo motor-gerador com autonomia de 24 horas em plena carga;
* Alimentação separada para os equipamentos de informática e telecomunicações.

**De acordo com ANSI/TIA-942, essas especificações permitirão a esse sistema elétrico ser classificado, no máximo, como:**

- ( ) Tier I
- ( ) Tier II
- ( ) Tier III
- ( ) Tier IV

---

### Questão 4
**Considerando a necessidade de continuidade exigida pelo sistema de distribuição de energia em um Datacenter, além de normas e conceitos relacionados, é correto afirmar:**

- ( ) O uso das chaves de comutação automática (**ATS**) são fundamentais ao fornecimento contínuo de energia, em especial na *Computer Room*, que terá sua alimentação alternada entre o sistema UPS e o gerador.
- ( ) Independente de sua classificação quanto à disponibilidade e à redundância, é recomendado para o sistema elétrico, no mínimo, ter uma fonte alternativa de energia, um sistema UPS e um sistema de aterramento dedicado à *Computer Room*.
- ( ) Redundância do tipo **“N+2”** para grupos motores-geradores, sistemas UPS e topologia de distribuição de alimentação das cargas conectadas às cargas críticas de TI são especificações mínimas **Tier IV**, de acordo com normas como a ANSI/TIA 942.
- ( ) Para mensurar e avaliar aspectos relacionados à eficiência energética em Datacenters, criou-se um índice chamado **PUE (Power Usage Effectiveness)**, que relaciona o consumo dos equipamentos críticos de TI com o consumo total do site, de forma que quanto menor for o seu valor, melhor será a eficiência energética.

---

### Questão 5
**A estrutura de backbone em um datacenter, conhecida como AS (*autonomous system*), deve possuir links de fornecedores variados, com o objetivo de manter o fornecimento de serviços, mesmo havendo falha em uma dessas conexões:**

- ( ) Certo
- ( ) Errado

---

### Questão 6
**Julgue o item a seguir: Se a classificação da parte elétrica de um data center for TIER 3 e a da parte mecânica for TIER 2, a classificação global desse data center será TIER 3:**

- ( ) Certo
- ( ) Errado

---

### Questão 7
**A redundância 2N de um data center adiciona um módulo, caminho ou sistema ao mínimo necessário para satisfazer o requisito básico:**

- ( ) Certo
- ( ) Errado

---

### Questão 8
**Segundo a norma ANSI/TIA 942, quais as regras aplicáveis para a classificação do Data Center em quatro níveis independentes de Tiers?**

- ( ) Redundância.
- ( ) Telecomunicação.
- ( ) Arquitetura e estrutural.
- ( ) Elétrica e Mecânica.
- ( ) Todas as alternativas anteriores.

---

### Questão 9
**Quais são os 4 níveis de Tier dos Data Centers?**

- ( ) Tier 1 – Básico, Tier 2 – Componentes Redundantes, Tier 3 – Sistema Auto Sustentado e Tier 4 – Alta Tolerância a Falhas.
- ( ) Tier 1 – Componentes Redundantes, Tier 2 – Básico, Tier 3 – Sistema Auto Sustentado e Tier 4 – Alta Tolerância a Falhas.
- ( ) Tier 1 – Básico, Tier 2 – Componentes Redundantes, Tier 3 – Alta Tolerância a Falhas e Tier 4 – Sistema Auto Sustentado.
- ( ) Tier 1 – Básico, Tier 2 – Alta Tolerância a Falhas, Tier 3 – Sistema Auto Sustentado e Tier 4 – Componentes Redundantes.

---

### Questão 10
**Como deve ser construído o sistema de aterramento?**

- ( ) Um aterramento isolado para o Data Center e outro para o para-raios, eletrocalhas, racks e piso elevado.
- ( ) Um aterramento isolado para o para-raios e outro para o Data Center, eletrocalhas, racks e piso elevado.
- ( ) Um aterramento isolado para o para-raios e eletrocalhas, e outro para o Data Center, racks e piso elevado.
- ( ) Um aterramento isolado para o para-raios, racks e piso elevado, e outro para o Data Center e piso elevado.

---

### Questão 11
**Ao se elaborar um Projeto de Rede desejando-se um ambiente com total redundância da infraestrutura do Data Center (elétrica, climatização, rede) deve-se optar por um:**

- ( ) Data Center Tier I ou Data Center Tier II
- ( ) Data Center Tier II ou Data Center Tier IV
- ( ) Data Center Tier I ou Data Center Tier III
- ( ) Data Center Tier III ou Data Center Tier IV

---

### Questão 12
**A SATC está com planos de padronizar sua estrutura de Data Center de acordo com a certificação Tier III. Para isso, foi designado um analista de TI para realizar o levantamento das características que o Data Center deve atender:**

1.  Dispor de switchs e roteadores operando com fontes redundantes.
2.  Possuir pé-direito de, no mínimo, 3 metros de altura.
3.  Estar localizado a mais de 1,6 km de aeroportos.
4.  Ter apenas 1 link com operadora de telecomunicações.
5.  Dispor de equipe de manutenção e suporte 24x7.

**Estão CORRETAS:**

- ( ) I, II, III e V.
- ( ) II, III e V.
- ( ) I, II, IV, V.
- ( ) I, III, IV e V.
- ( ) I, II e III.