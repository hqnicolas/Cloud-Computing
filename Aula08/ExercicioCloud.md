Questão:1
Um arquiteto de soluções está projetando um sistema de observabilidade unificado para uma empresa que adotou uma estratégia multicloud. A aplicação principal está hospedada na AWS, um banco de dados analítico roda na Azure e um cluster Kubernetes para processamento de dados está na GCP (Google Cloud Platform). Além disso, a empresa está avaliando migrar um workload para a OCI (Oracle Cloud Infrastructure) no próximo trimestre.

O arquiteto precisa definir, para cada provedor de nuvem, qual é o serviço nativo e específico responsável por coletar, armazenar e disponibilizar as métricas de infraestrutura e aplicação (como uso de CPU, memória, latência e contagem de requisições).

Pergunta: Quais são, respectivamente, os serviços de métricas nativos e específicos para AWS, Azure, GCP e OCI?

Para responder à sua questão sobre os serviços nativos de métricas em um cenário multicloud, os serviços específicos de cada provedor citados são:

*   **AWS (Amazon Web Services):** **Amazon CloudWatch**. É o serviço que coleta e visualiza métricas em tempo real, permitindo a criação de alarmes e respostas automáticas a mudanças nos recursos da AWS.
*   **Azure (Microsoft Azure):** **Azure Monitor**. É a solução abrangente para coletar, analisar e agir sobre a telemetria de ambientes em nuvem e locais, incluindo o recurso específico de *Azure Monitor Metrics*.
*   **GCP (Google Cloud Platform):** **Cloud Monitoring**. Faz parte do *Google Cloud Operations Suite* (antigo Stackdriver) e fornece visibilidade sobre o desempenho, tempo de atividade e integridade geral de aplicações e infraestrutura.
*   **OCI (Oracle Cloud Infrastructure):** **OCI Monitoring**. Este serviço permite monitorar recursos de forma ativa e passiva usando métricas para verificar o estado de integridade e o desempenho dos ativos na nuvem Oracle.

Esses serviços são fundamentais para uma estratégia de observabilidade, pois permitem que o arquiteto de soluções centralize dados críticos como uso de CPU, latência de rede e consumo de memória, mesmo que distribuídos em diferentes ecossistemas de nuvem.