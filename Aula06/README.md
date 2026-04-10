## Norma ANSI/TIA-942
**Telecommunications Infrastructure Standard for Data Centers**
---

### TIA-942 – O que é?
- Documento padrão que define os requisitos mínimos para um projeto de instalação de um Data Center (DC).
- **DC:** Construção ou parte de um edifício cuja função primária é alojar uma sala de computadores e suas áreas de suporte.

---

### TIA-942 – Requisitos
Fazem parte dos requisitos mínimos deste documento a avaliação de:
- HVAC
- Energia
- Iluminação
- Arquitetura
- Piso elevado
- Redundância
- Controle de acesso
- Prevenção de incêndio
- Cabeamento estruturado

<img width="756" height="714" alt="image" src="https://github.com/user-attachments/assets/2b4179c0-14ea-4d52-9189-c62afa856784" />


---

### TIA-942 – Faz Referência
- ANSI/TIA/EIA-568-B.1: Commercial Building Telecommunications Cabling Standard; Part 1: General Requirements.
- ANSI/TIA/EIA-568-B.2: Commercial Building Telecommunications Cabling Standard; Part 2: Balanced Twisted-Pair Cabling Components.
- ANSI/TIA/EIA-568-B.3-2000: Optical Fiber Cabling Components Standard.
- ANSI/TIA-569-B: Commercial Building Standard for Telecommunications Canaletas and Spaces.
- ANSI/TIA/ΕΙΑ-606-A-2000: Administration Standard for Commercial Telecommunications Infrastructure.
- ANSI/TIA/EIA-J-STD-607-2001: Commercial Building Grounding (Earthing) and Bonding Requirements for Telecommunications.
- ANSI/TIA-758-A: Customer-Owned Outside Plant Telecommunications Cabling Standard.
- ANSI/NFPA 70-2002: National Electrical Code.
- ANSI/NFPA 75-2003: Standard for the protection of information technology equipment.
- ANSI T1.336: Engineering requirements for a universal telecommunications frame.
- ANSI T1.404: Network and customer installation interfaces - DS3 and metallic interface specification.
- ASHRAE: Thermal Guidelines for Data Processing Environments.
- Telcordia GR-63-CORE: Requirements, physical protection.
- Telcordia GR-139-CORE: General Requirements for central office coaxial cable.

<img width="894" height="618" alt="image" src="https://github.com/user-attachments/assets/e95a23db-cdde-4d7a-b598-103be7037150" />


---

### TIA-942 - Topologia Básica
Os elementos básicos da estrutura do sistema de cabeamento do data center relacionam como eles estão configurados para criar o sistema total:
a) Cabeamento horizontal;
b) Cabos de backbone;
c) Conexão cruzada na sala de entrada ou na área de distribuição principal;
d) Conexão cruzada principal (MC) na área de distribuição principal;
e) Conexão cruzada horizontal (HC) na sala de telecomunicações, área de distribuição horizontal ou principal área de distribuição;
f) Saída da zona ou ponto de consolidação na área de distribuição da zona;
g) Tomada na área de distribuição de equipamentos.

<img width="841" height="562" alt="image" src="https://github.com/user-attachments/assets/606b283e-74bb-4897-902c-36d25c5c85f3" />


---

### TIA-942 - Espaços do Data Center
- **EF:** Sala de Entrada
- **TR:** Sala de Telecom
- **MDA:** Main Distribution Area "Cross-connect"
- **SDA:** Secondary Distribution Area
- **HAD:** Horizontal Distribution Area
- **ZDA:** Zone Distribution Area
- **EDA:** Equipment Distribution Area
- **CA:** Caixa de Acesso (Área de Suporte ao DC)

---

### TIA-942 - Espaços e Definições

**CAIXA DE ACESSO**
É a caixa externa localizada no limite entre a infraestrutura dos provedores de acesso e a infraestrutura do data center.

**SALA DE ENTRADA (EF)**
- Espaço para interface entre o cabeamento estruturado do DC e o cabeamento entre edifícios ou de operadoras de telecomunicações.
- Área na qual as instalações pertencentes ao provedor de acesso promovem a interface com o sistema de cabeamento.
- Aloja equipamentos de transmissão do provedor e é o ponto de demarcação.

**SALA DE TELECOMUNICAÇÕES (TR)**
Suporta o cabeamento para as áreas externas à sala de computadores, localizada fora dela.

<img width="720" height="563" alt="image" src="https://github.com/user-attachments/assets/d302dc87-ce12-47d8-bf44-0527d7b1279d" />


**MDA (Main Distribution Area)**
- Inclui o "Cross-Connect" principal (ponto central de distribuição).
- Aloca Switches Core e grandes roteadores.
- Área principal para manobras com racks abertos para Patch Panels.

**HDA (Horizontal Distribution Area)**
- Utilizada para conexão com as áreas de equipamentos.
- Espaço intermediário para ativos e cross-conexões.
- Reduz o cabeamento metálico entre MDA e EDA.

**EDA (Equipment Distribution Area)**
Espaço destinado para equipamentos de ponta, como servidores e equipamentos de storage.

---

### TIA-942 – Espaços e Equipamentos

**CAIXA DE ACESSO**
Sem equipamentos ativos; no máximo caixas de proteção de fusões ópticas.

**SALA DE ENTRADA (Entrance Room)**
- Roteadores, modens ópticos, interfaces coaxiais, metálicas e/ou ópticas.
- Pode existir mais de uma e pode estar junto do MDA.

**SALA DE TELECOMUNICAÇÕES**
- Switches e cabeamento das áreas administrativas e de suporte.
- Terminais de acesso (KVM).

**MDA – MAIN DISTRIBUTION AREA**
- MC (Main cross-connect) e HC (Horizontal cross-connect).
- Switches core, roteadores core, switches SAN, switches NAS, racks de cross-conexão, PABX.
- No mínimo uma MDA deve existir.

**HDA – ÁREA DE DISTRIBUIÇÃO HORIZONTAL**
- Switches de acesso (LAN, SAN), racks de patch panels e painéis ópticos.

**ZDA – ÁREA DE DISTRIBUIÇÃO POR ZONA**
- Não pode ter ativos de rede.
- Espelho das conexões de servidores; até 288 pontos por ZDA.

**EDA – ÁREA DE EQUIPAMENTOS**
- Pode receber switches SAN/NAS.
- Racks de servidores (DELL, HP, IBM) e ativos como IBM AS400, EMC Storage.
- Racks de cabeamento para espelho das conexões de ativos.

<img width="958" height="553" alt="image" src="https://github.com/user-attachments/assets/874aa942-1564-43cd-92ca-7763c5e1f219" />


---

### TIA-942 – Etapas do Projeto
- Mensurar capacidade máxima (espaço, energia e refrigeração) considerando tendências.
- Fornecer requisitos de instalação (energia, resfriamento, segurança, carga do piso, aterramento) para arquitetos e engenheiros.
- Coordenar planejamentos das áreas do DC.
- Criar planta com posicionamento de equipamentos, cross-connect e requisitos de calhas.
- Obter planta atualizada com equipamentos elétricos e mecânicos.
- Projetar o cabeamento estruturado.

---

### TIA-942 – Computer Room

**Requisitos Gerais:**
- Ambientalmente controlado conforme ANSI/NFPA 75-2003.
- Carga do piso deve incluir equipamentos e mídias.
- Prever espaços livres em cada lado do equipamento e fluxo de ar.
- Atender requisitos de energia DC e comprimentos de conectividade.

**Localização:**
- Evitar locais que limitem a expansão.
- Acessibilidade para entrega de grandes equipamentos.
- Distante de interferência eletromagnética (transformadores, motores, geradores).
- Não deve possuir janelas exteriores.

**Acessos e Equipamentos:**
- Portas com controle de acesso apenas para autorizados.
- Equipamentos elétricos até 100 kVA podem estar na sala (exceto baterias líquidas).
- UPS maiores que 100 kVA ou com baterias líquidas devem estar em sala separada.
- Altura mínima de 2,6 m do piso acabado até obstáculos (sprinklers, luminárias).
- Manter 46 cm de espaço livre para sprinklers.

**Iluminação:**
- Mínimo de 500 lux no plano horizontal e 200 lux no plano vertical (medidos a 1 m de altura).
- Alimentação independente dos equipamentos de telecomunicações.
- Posicionada nos corredores entre gabinetes.

**Requisitos Arquitetônicos:**
- Portas: Mínimo 1 m x 2,13 m, sem soleira, abrindo para fora ou de correr. Sem poste central para facilitar acesso.
- Altura do Piso:
    - Tier I: 30 cm
    - Tier II: 46 cm
    - Tier III e IV: 76/91 cm

**Controle de Temperatura e Umidade:**
- Temperatura: 18 ºC a 27 ºC.
- Umidade relativa: 40% a 55%.
- Variação máxima: 5 ºC por hora.
- Ar-condicionado conectado a gerador, funcionando 24/365.

<img width="503" height="302" alt="image" src="https://github.com/user-attachments/assets/21641e55-dae2-4680-85a5-32d09e24271b" />


**Energia:**
- Circuitos de alimentação de ativos exclusivos e redundantes (no-break, gerador).
- Tomadas de serviço independentes: uma a cada 3,65 m nas paredes.

---

### TIA-942 – Resfriamento e Corredores
- Aplicar corredores quentes e frios com isolamento (containment).
- Entrada de ar dos equipamentos voltada para o corredor frio.
- Racks com portas perfuradas.
- Regular pressão do ar frio conforme a geração de calor dos racks.
- Utilizar painéis fechados em espaços não usados nos racks.
- Conceito “dark data center”.

  <img width="1036" height="570" alt="image" src="https://github.com/user-attachments/assets/1e829f8e-2f3c-4048-814d-dcdea340954a" />


---

### TIA-942 – Cabeamento
- Recomenda-se o uso de cabos tipo LSZH (Low Smoke Zero Halogen), CMP ou outros com baixa propagação de chama e fumaça (normas NBR 14705 e NBR 5410).

---

### TIA-942 – Classificação (Tiers)
A classificação considera 4 níveis para arquitetura, telecomunicações, elétrica e mecânica:

**Níveis de Redundância:**
- **N:** Sem redundância.
- **N+1:** Pelo menos uma redundância (ex: um no-break extra).
- **N+2:** Duas redundâncias a mais.
- **2N:** Redundância completa (ex: duas alimentações de subestações diferentes).
- **2(N+1):** Redundância para cada equipamento individualmente.

**Tier I – Básico:**
- Único caminho de distribuição; sem redundância de rotas físicas.
- Falha ou manutenção causa interrupção total ou parcial.
- Downtime permitido: até 28,8 horas anuais.

**Tier II – Componentes Redundantes:**
- Módulos redundantes em ativos (fontes, placas).
- Cabeamento de backbone pode ter fibras redundantes.
- Requer dois caminhos de entrada (ER) com separação física de 20 m recomendada.
- UPS redundante (N+1) e sistema de gerador.
- Downtime permitido: até 22,0 horas anuais.

**Tier III – Sistema Auto Sustentado:**
- Atendido por pelo menos duas operadoras distintas.
- Duas salas de entrada (ER) separadas por 20 m em zonas de proteção distintas.
- Caminhos redundantes entre ER, MDA e HDA.
- Manutenção permitida sem paralisação dos serviços.
- Downtime permitido: até 1,6 horas anuais.

**Tier IV – Sem Tolerância a Falhas:**
- Todo o cabeamento de backbone redundante e protegido por caminhos fechados.
- Equipamentos ativos redundantes com alimentação dupla e comutação automática.
- Recomendada MDA secundária em zona de proteção contra fogo separada.
- Disponibilidade elétrica 2(N+1) com duas fontes de energia pública de diferentes subestações.
- HVAC com múltiplas unidades redundantes e fontes de energia distintas.
- Downtime permitido: até 0,4 horas anuais.

<img width="1117" height="726" alt="image" src="https://github.com/user-attachments/assets/cc0c711e-8a25-4219-afbf-b54144e6bd47" />

**Nota final:** A classificação do Data Center é determinada pelo menor nível atingido entre as áreas avaliadas.
