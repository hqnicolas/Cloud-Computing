## 1. Introdução aos Sistemas Operacionais

A evolução dos sistemas operacionais permitiu que saíssemos de modelos subutilizados para sistemas altamente eficientes:

* **Sistemas Monotarefa:** Suportavam apenas um processo por vez, resultando em subutilização de hardware (CPU, memória e disco).

<img width="794" height="250" alt="image" src="https://github.com/user-attachments/assets/d03bfa77-5d67-4441-b08b-621e5912acb4" />


* **Sistemas Multitarefa:** Permitem que o processador suspenda uma tarefa que aguarda dados externos para executar outra.

<img width="892" height="375" alt="image" src="https://github.com/user-attachments/assets/6a3b1d16-9f58-4bfb-b976-d82a7cc544ab" />


* **Preempção:** Mecanismo que permite retirar um recurso (como o processador) de uma tarefa para entregá-lo a outra.



---

## 2. Processos e Threads

A estrutura de execução de um sistema é dividida em dois conceitos principais:

### Processos

* Funciona como um **contêiner de recursos** para uma ou mais tarefas.


* Cada processo possui um identificador único chamado **PID** (Process Identifier).


* **Isolamento:** Os processos são isolados por hardware e não compartilham memória entre si, garantindo segurança.

### Threads (Linhas de Execução)

* É uma linha de execução **dentro de um processo**.


* Cada thread possui seu próprio estado de processador e pilha.


* **Compartilhamento:** Diferente dos processos, threads "irmãs" compartilham a mesma memória atribuída ao processo pai.



---

## 3. Concorrência vs. Paralelismo

Embora parecidos, os conceitos possuem distinções técnicas importantes:

| Conceito | Definição | Analogia |
| --- | --- | --- |
| **Concorrência** | Lidar com várias coisas ao mesmo tempo (gestão de execução). | Fila de Drive-Thru. |
| **Paralelismo** | Fazer várias coisas simultaneamente através de múltiplos núcleos. | Cabines de Pedágio. |

Em processadores **Multi-core**, um único processo pode ter várias threads rodando simultaneamente em núcleos diferentes, atingindo o paralelismo real.

---

## 4. Modelos de Programação

Os fluxos de execução determinam como o código é escrito e processado:

1. **Modelo Síncrono:** Uma operação deve ser finalizada para que a próxima inicie (Ex: PHP).


2. **Modelo Assíncrono:** Operações alternam o controle de execução sem esperar o término da anterior (Ex: Go).



---

## 5. Arquitetura de Hardware e Memória

O sistema operacional atua como gestor dos recursos físicos:

### Gestão de Memória

* **Volátil (Primária):** Registradores, Cache e RAM. Perdem dados sem energia, mas são muito rápidas.


* **Não Volátil (Secundária):** HDs, SSDs e PenDrives. Armazenamento permanente.


* **Memória Virtual (SWAP):** Utilizada quando a memória principal (RAM) não comporta a demanda.



### Evolução dos Processadores

* **Intel 4004 (1971):** 4.500 transistores e clock de 2MHz.


* **Intel Core i7 (Moderno):** Bilhões de transistores, múltiplos núcleos e clocks acima de 3.0 GHz.



---

## 6. Gestores do Sistema Operacional (Resumo)

<img width="1027" height="558" alt="image" src="https://github.com/user-attachments/assets/af012b09-f556-419e-8ac5-7365fe41530c" />


O S.O. é composto por softwares específicos para cada função:

* **Memory Manager:** Alocação de memória.


* **File Manager:** Controle do sistema de arquivos.


* **Processor Manager:** Coordenação da execução de processos.


* **Device Manager:** Controle de hardware (I/O).



---

### Atividade Prática

Para consolidar esses conhecimentos, busque exemplos de programação **síncrona** e **assíncrona** na linguagem que você mais utiliza ou no seu sistema operacional de preferência.
