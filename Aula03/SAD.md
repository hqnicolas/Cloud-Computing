# Cloud Computing: Sistemas de Arquivos Distribuídos (SAD)

---

## 1. Introdução aos SADs

Os Sistemas de Arquivos Distribuídos (SADs) permitem o compartilhamento de informações por meio de recursos de hardware e software.

> 
> **Nota:** Quando bem projetado, um SAD oferece acesso a arquivos em um servidor com desempenho e confiabilidade semelhantes aos de arquivos em discos locais.
> 
> 

---

## 2. Arquitetura Cliente/Servidor


Os sistemas são organizados seguindo o modelo cliente/servidor, apresentando duas abordagens principais:

1. **Modelo de Acesso Remoto:** As requisições são enviadas para acessar o arquivo que permanece no servidor.


2. **Modelo de Carga/Atualização:** O arquivo é transferido para o cliente, os acessos são feitos localmente e, ao concluir, o arquivo (novo) é retornado ao servidor.



---

## 3. Características Importantes

* Clientes remotos acessando arquivos em servidores distintos.


* Esquema de compartilhamento bem estruturado.


* Clientes dispersos geograficamente.


* Ponto de vista centralizado para o usuário.



---

## 4. Por que utilizar um SAD?

A necessidade de um SAD surge principalmente para resolver o **compartilhamento de recursos**:

* **Espaço em disco:** Evita que cada máquina precise armazenar localmente todos os arquivos que acessa.


* **Administração:** Facilita processos de backup e gerência centralizada.


* **Acesso:** Permite acessar arquivos particulares de diferentes computadores.



---

## 5. Funcionalidades e Interfaces

O SAD provê acesso aos dados através de interfaces que permitem:

* Abrir, fechar e checar o estado de arquivos.


* Ler e escrever dados.


* Bloquear arquivos ou partes deles (concorrência).


* Listar diretórios.


* Apagar e renomear arquivos ou diretórios.



---

## 6. Requisitos de Suporte

* **Transparência:** O arquivo deve ser acessado de forma transparente em qualquer nó, independentemente da localização.


* **Mobilidade do Usuário:** Flexibilidade para o usuário trabalhar em diferentes nós em momentos distintos.



---

## 7. Formas de Armazenamento

Existem duas formas principais de organizar o armazenamento:

1. **Centralizado:** O sistema de arquivo inteiro fica em um único servidor.


2. **Distribuído (Master/Slave):** Arquivos distribuídos em vários discos de diferentes computadores.



---

## 8. Serviços Ofertados

* **Serviço de Nomes:** Indica a localização do arquivo dado seu nome ou caminho.


* **Serviço de Arquivo:** Fornece as operações sobre os arquivos (leitura, escrita, etc.).


* **Serviço de Diretórios:** Mantém a organização hierárquica (diretórios e subdiretórios).



---

## 9. Atributos de Qualidade do SAD

Para ser eficiente, um SAD busca as seguintes características:

| Característica | Descrição |
| --- | --- |
| **Tolerância a Falhas** | O sistema não pode perder informações ou ficar indisponível se um servidor cair. |
| **Acesso Concorrente** | Vários usuários acessando o mesmo arquivo sem perda de performance ou danos. |
| **Replicação** | Aumenta a confiança e eficiência do serviço. |
| **Escalabilidade** | Capacidade de prever o crescimento de nós e usuários. |
| **Segurança** | Controle de acesso e autenticação de clientes. |
| **Consistência** | Todas as cópias devem agir como se fossem uma única. |

---

## 10. Exemplo: Network File System (NFS)

O NFS é um exemplo clássico de SAD com arquitetura cliente-servidor, muito popular em sistemas Unix.

* **Visão Padronizada:** O servidor fornece uma visão padronizada do seu sistema local.


* **VFS:** Utiliza um Sistema de Arquivo Virtual (Virtual File System).


* **RPC:** As requisições ao servidor são feitas via *Remote Procedure Call*.



---

## 11. SAD Baseados em Cluster

Utilizados frequentemente para computação paralela:

* **File Stripping:** Arquivos divididos em "tiras" através dos servidores para aumentar a performance.


* **Efetividade:** Funciona bem para dados estruturados e regulares; menos efetivo para dados irregulares de uso geral.



---

## 12. Exemplos de SAD no Mercado

Alguns dos principais sistemas utilizados incluem:

* GFS (Google FileSystem) e Hadoop (HDFS).
* GlusterFS, Ceph e Lustre.
* AFS (Andrew FileSystem) e CODA.
