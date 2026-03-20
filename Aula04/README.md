# Cloud Computing: On-Premise VS Cloud Servers 
---

## Servidor Cloud OR Servidor Local? 

### Diferentes tipos de infraestrutura 

**Servidores On-Premise:** 
* São hardwares físicos que ficam armazenados na sala da empresa. 
* Exigem controle de temperatura por ar-condicionado para evitar o superaquecimento. 
* Quase sempre requerem a utilização de um nobreak para prevenir quedas e picos repentinos de energia. 
* Exigem uma rotina de backup para precaver possíveis falhas ou avarias no dispositivo. 

**Servidores Cloud:** 
* São contratados como um serviço junto a um provedor que se responsabiliza por toda a infraestrutura, manutenção e recursos periféricos. 
* Esse modelo permite que o departamento de TI da sua empresa se concentre em outras demandas. 

---

### Investimentos necessários 

**Servidores On-Premises:** 
* Precisam de um grande aporte inicial, incluindo hardwares, sistema operacional e periféricos. 
* Exigem investimento em sala do servidor físico, além de treinamento da equipe de TI para instalar e prestar a manutenção corretamente de forma cíclica. 
* Possuem custos com rotinas de suporte, o que pode envolver horas de trabalho e atualização de softwares, antivírus e sistema operacional. 

**Servidores Cloud:** 
* Requerem o pagamento de mensalidades, o que diminui a necessidade de investimentos iniciais, compra de itens menos essenciais ou horas de manutenção da sua equipe. [cite:
* Dependendo do modelo de serviço escolhido (SaaS, PaaS ou IaaS), faz-se necessário ter uma pessoa ou equipe especializada para prestar suporte e manutenção de forma cíclica. 

---

### Redes 

* **Servidores On-premise:** Requerem a instalação e configuração de equipamentos de redes, agregando mais custos na implantação de um Data Center local.  À medida que sua rede cresce, maior será a complexidade dela. 
* **Servidores Cloud:** Alguns componentes adicionais podem adicionar a comunicação e segurança necessárias a esta rede, como por exemplo, uma virtual private cloud (VPC). 

---

### Recuperação de dados e backup 

* **Servidores On-premise:** No contexto de servidores locais, o gestor de TI passa a ser o responsável por uma recuperação em caso de desastre ou falha para garantir a continuidade dos negócios. 
* **Servidores Cloud:** Ao contratar um serviço em nuvem, a parte de backup já está incluída no pacote.  Assim, a responsabilidade de retornar as operações em caso de falha ou desastre é da empresa contratada. 

**Parâmetros principais de recuperação:** 
* **RPOs (Objetivos de Ponto de Recuperação):** Limitam o período de volta no tempo e definem a quantidade máxima permitida de dados perdidos em uma ocorrência de falha (desde o último backup válido). 
* **RTOs (Objetivo de Tempo de Recuperação):** Representam a quantidade de tempo que leva para se recuperar de um incidente até que as operações estejam novamente disponíveis para os usuários (período inativo do usuário). 

> *[Espaço reservado para a imagem da página 10: Gráfico ilustrando a linha do tempo de Last backup, Failure, Recovered data, Recovery Point e Recovery Time]* 

---

### Gerenciamento da Energia 

* **Servidores On-premise:** O abastecimento de energia é crucial e requer mão de obra especializada de engenharia elétrica, e não apenas de TI. 
* **Servidores Cloud:** A gestão energética fica a cargo do fornecedor dos serviços, que tem a responsabilidade de manter o SLA (Acordo de nível de serviço) contratado. 

---

### Gestão de cotas 

* **Servidores On-premise:** Sua cota de quantidade de solicitações, downstream e upstream dependem exclusivamente da capacidade de infraestrutura local. 
* **Servidores Cloud:** Sua cota vai depender do plano contratado.  Esses parâmetros podem ser acrescidos de acordo com a demanda; porém, à medida que a empresa cresce, o custo do cloud computing acaba sendo equivalente ao de montar uma infraestrutura própria. 

> *[Espaço reservado para a imagem da página 13: Imagens detalhando níveis de uso gratuito, limites e cotas de recursos da AWS]* 

---

## Considerações Finais e Conclusão 

Uma decisão errada de gestores de TI com pouco conhecimento é escolher a opção mais econômica num curto prazo de tempo, sem se atentar aos custos de manutenção a médio e longo prazo.  Uma boa prática para analisar com maior precisão qual solução seria mais vantajosa para o seu cenário é criar uma linha do tempo, contemplando e diluindo os valores de investimentos necessários ao longo de 3 ou 5 anos. 

Existe muita diferença entre ter um servidor Cloud e um On-Premise, e a diferença de investimentos pode ser facilmente calculada.  O provedor de serviços Cloud pode distribuir as despesas entre seus clientes, o que o torna mais barato do que uma solução local na maioria das vezes.  Contudo, é fundamental não se enganar sobre qual o serviço correto a ser contratado, pois uma escolha equivocada ("aventura" na nuvem) pode custar mais caro do que manter a infraestrutura em casa. 


