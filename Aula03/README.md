# Aula 03: Sistemas de Arquivos Distribuídos (SAD) e GlusterFS

Esta aula explora os conceitos fundamentais dos **Sistemas de Arquivos Distribuídos (SAD)**, suas características essenciais e um exemplo prático de implementação com o **GlusterFS**.

---

## 1. Sistemas de Arquivos Distribuídos (SAD)

Um Sistema de Arquivos Distribuído visa gerenciar o armazenamento de dados através de múltiplos servidores, apresentando-os como um único sistema de arquivos aos usuários.

### 1.1 Serviços Ofertados

Os SADs fornecem serviços cruciais para a gestão de dados:

*   **Serviço de Nomes:** Localiza arquivos a partir de seu nome ou caminho.
*   **Serviço de Arquivo:** Permite operações básicas sobre arquivos (leitura, escrita, etc.).
*   **Serviço de Diretórios:** Mantém a estrutura hierárquica de diretórios e subdiretórios.

### 1.2 Atributos de Qualidade

Para garantir eficiência e confiabilidade, um SAD busca as seguintes características:

*   **Tolerância a Falhas:** Garante que o sistema permaneça disponível e não perca dados mesmo com a falha de um servidor.
*   **Acesso Concorrente:** Permite que múltiplos usuários acessem o mesmo arquivo simultaneamente sem perda de desempenho ou integridade.
*   **Replicação:** Aumenta a confiança, disponibilidade e eficiência do serviço através de cópias de dados.
*   **Escalabilidade:** Capacidade de se adaptar ao crescimento de nós e usuários de forma eficiente.
*   **Segurança:** Implementa controle de acesso e autenticação para proteger os dados.
*   **Consistência:** Assegura que todas as cópias de um arquivo ajam como uma única entidade lógica.

### 1.3 Exemplo: Network File System (NFS)

O **NFS** é um exemplo clássico de SAD com arquitetura cliente-servidor, amplamente utilizado em sistemas Unix para fornecer uma visão padronizada do sistema de arquivos de um servidor.

---

## 2. GlusterFS: Sistema de Arquivos Distribuído e Escalável

O **GlusterFS** é uma solução robusta e de **código aberto** para gerenciamento de armazenamento em larga escala, ideal para ambientes que exigem alta disponibilidade e escalabilidade.

### 2.1 O que é GlusterFS?

É um sistema de arquivos distribuído *open source* projetado para suportar:

*   **Vários petabytes** de armazenamento.
*   **Milhares de clientes** conectados simultaneamente.
*   Demandas crescentes **sem perda de desempenho**.

Sua função principal é agregar recursos de armazenamento de múltiplos servidores em um único **namespace global**, eliminando a necessidade de um servidor central de metadados, o que o torna altamente escalável e resiliente.

### 2.2 Arquitetura e Conceitos-Chave

A arquitetura do GlusterFS é focada na eliminação de gargalos tradicionais:

*   **Bricks:** São as unidades básicas de armazenamento, que representam diretórios exportados em servidores individuais que contribuem para a capacidade do volume.
*   **Volumes:** São coleções lógicas de *bricks*, configuráveis em diferentes modos (distribuído, replicado, disperso ou híbrido) para atender a diversas necessidades de redundância e desempenho.

---

Para mais detalhes sobre a implementação e configuração do GlusterFS, consulte a documentação específica.