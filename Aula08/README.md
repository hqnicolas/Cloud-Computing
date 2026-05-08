# Gestão de Data Center: Métricas

## FUNDAMENTOS

### Conceitos Fundamentais: Medida, Métrica e Indicador

Segundo o BPM CBOK versão 3.0, a gestão por métricas exige a compreensão precisa de três conceitos inter-relacionados. Eles possuem definições técnicas distintas e papéis complementares no processo de tomada de decisão em TI.

* **Medida:** É a quantificação de dados em um padrão e qualidade aceitáveis. Representa o dado bruto coletado em uma unidade padronizada.
* *Exemplos:* metros, Mbps (velocidade de link), graus Celsius (temperatura), watts (consumo elétrico). É o ponto de partida essencial.


* **Métrica:** Uma extrapolação de medidas; uma conclusão baseada em dados finitos. É a relação entre várias medidas que gera uma informação mais elaborada.
* *Exemplos:* Taxa de utilização de CPU ao longo do tempo ou percentual de perda de pacotes.


* **Indicador:** Uma representação simples ou intuitiva de uma métrica ou medida para facilitar a interpretação em relação a uma referência ou alvo. O indicador traduz a métrica em informação acionável para gestores em dashboards.
* *Exemplo:* "Disponibilidade do link principal = 99,8% (meta: 99,5%)".



Não existe uma "receita de bolo" universal; os índices devem ser definidos conforme o contexto organizacional, SLAs e objetivos estratégicos.

---

## INFRAESTRUTURA

### Disponibilidade de Infraestrutura

A disponibilidade é o pilar mais crítico da operação. O monitoramento proativo antecipa falhas e reduz o MTTR (Mean Time To Repair).

**Ativos Monitoráveis:**

* **Links de Internet:** Disponibilidade, latência e consumo de banda.
* **Portas de Switch:** Tráfego, erros CRC e colisões.
* **Temperatura e Umidade:** Sensores ambientais em racks para prevenir danos físicos por superaquecimento.
* **Corrente Elétrica:** Sensores para identificar picos de consumo e anomalias.
* **UPS e Energia:** Status de no-breaks, baterias e PDUs inteligentes.

---

## REDE

### Tráfego de Internet: Análise de Métricas de Banda

O monitoramento em tempo real identifica gargalos e anomalias de segurança (como ataques DDoS). A análise considera média, mínimo e máximo para dimensionar a margem de segurança do link.

| Métrica | Entrada | Saída |
| --- | --- | --- |
| Média | 5,17 Mbps | 399,33 Kbps |
| Último | 3,2 Mbps | 293,27 Kbps |
| Mínimo | 6,52 Mbps | 529,93 Kbps |
| Média (histórico) | 10,23 Mbps | 1,51 Mbps |

A assimetria (download maior que upload) é comum; para data centers, recomendam-se links dedicados simétricos.

---

## INFRAESTRUTURA FÍSICA

### Monitoramento Ambiental e Elétrico

* **Sensores de Temperatura e Umidade:** Recomendação ASHRAE de 18°C a 27°C para temperatura e 40% a 60% para umidade. Conectividade USB ou Wi-Fi facilita a instalação.
* **Sensor de Corrente Não Invasivo:** Sensores tipo *clamp-on* permitem monitorar o consumo sem interromper o fluxo de energia. Essenciais para calcular o **PUE (Power Usage Effectiveness)**.

---

## SERVIDORES

### Performance de Servidores: Monitoramento Proativo

* **Memória:** Monitorar RAM para identificar vazamentos e evitar o uso de *swap*.
* *Ferramentas:* `free`, `vmstat`, `htop`, `pmap`, `sar`.


* **CPU:** Picos sustentados acima de 80% indicam necessidade de otimização ou upgrade.
* *Ferramentas:* `vmstat`, `mpstat`, `iostat`, `sar`, `pidstat`.


* **I/O (Entrada/Saída):** Identifica discos com alta latência e gargalos de throughput.
* *Ferramentas:* `iostat`, `vmstat` (coluna wa), `sar`.


* **Rede:** Identifica problemas de conectividade e gargalos de throughput.
* *Ferramentas:* `tcpdump`, `ping`, `ifstat`, `iptraf`, `vnstat`.



---

## SERVICE DESK

### Métricas de Chamados: Gestão de Operações de Suporte

O dashboard de operações é a ferramenta central para avaliar a eficiência da equipe.

**Indicadores-Chave de Performance (KPIs):**

* **TMA (Tempo Médio de Atendimento):** Agilidade no primeiro contato.
* **SLA de Cumprimento:** % de chamados resolvidos no prazo (meta comum: >95%).
* **TMR (Tempo Médio de Resolução):** Eficiência operacional total.
* **Ranking por Setor/Problema:** Identifica padrões para ações preventivas.

**Análise de Dashboard:** Permite observar a relação entre chamados abertos e fechados, horas trabalhadas por dia e a performance individual dos analistas para equilibrar a carga de trabalho.

---

## SEGURANÇA

### Monitoramento de Portas e Dispositivos

O rastreamento de portas abertas em estações de trabalho é uma prática essencial de *hardening*.

**Portas Comuns e Serviços:**

* **HTTP:** 80
* **FTP:** 20/21
* **Telnet:** 23 (Deve ser evitada em estações)
* **DNS:** 53
* **SNMP:** 161/162 (Recomendado v3 com autenticação)
* **SMB:** 445 (Não deve estar ativo em estações comuns)

---

## NEGÓCIO

### Retorno sobre Investimento (ROI) em TI

O ROI conecta investimentos técnicos a resultados financeiros.

**Fórmula:**


$$ROI = \frac{(Benefício Total - Custo Total)}{Custo Total} \times 100$$

**Exemplo Prático:** Um upgrade de link de R$ 5.000/mês que elimina 12h de lentidão para 80 colaboradores (custo hora R$ 50) gera uma economia de R$ 48.000/mês, resultando em um ROI de 860%.

---

## FERRAMENTAS

### Automatizando a Gestão de Métricas

* **NetData:** Monitoramento em tempo real, agente leve, ideal para visibilidade imediata.
* **Zabbix:** Solução robusta e completa para ambientes de médio e grande porte. Suporta mapas de rede e alertas multicanal.
* **Nagios XI:** Focado em disponibilidade e alertas, amplamente adotado em ambientes críticos.
* **Cacti / MRTG:** Tradicionais para monitoramento de tráfego de rede via SNMP e gráficos históricos.
* **Webmin:** Administração baseada em web para servidores Linux/Unix.

**Recomendação:** NetData para pequenos/médios ambientes; Zabbix ou Nagios XI para data centers corporativos.