## 1. O que são Sistemas de Arquivos?

Os sistemas de arquivos são uma parte essencial dos sistemas operacionais, fornecendo uma **visão abstrata dos dados persistentes**. Eles são responsáveis pelo serviço de nomes, acesso aos arquivos e sua organização geral.

Enquanto um processo está em execução, ele pode armazenar informações em seu espaço de endereçamento, mas essa capacidade é limitada e os dados são perdidos quando o processo termina. Para solucionar isso, o sistema operacional utiliza a abstração do **arquivo**.

### Requisitos Essenciais para Armazenamento

Para que o armazenamento de longo prazo seja eficiente, três requisitos devem ser atendidos:

1. Armazenar grandes quantidades de informações.


2. Permanência dos dados após o término do processo.


3. Acesso simultâneo por múltiplos processos.



---

## 2. Abstrações: Arquivos e Diretórios

O sistema operacional utiliza conceitos específicos para organizar a informação:

* **Arquivo:** Definido como uma sequência de bytes com uma estrutura interna específica e atributos como tamanho, datas de acesso e proprietário.


* **Diretório:** Um arquivo especial que mapeia nomes para identificadores, podendo conter subdiretórios em uma estrutura de árvore.



<img width="172" height="138" alt="image" src="https://github.com/user-attachments/assets/ab77bf04-4e34-4ccf-be6a-46c7807c3513" />


---

## 3. Estrutura e Organização do Disco

Um sistema de arquivos organiza os dados de forma que o SO possa localizá-los rapidamente através de um **índice**. O processo de dividir um dispositivo em seções é chamado de **particionamento**, e a aplicação de um sistema de arquivos a essa partição é a **formatação**.

### Componentes da Estrutura de Disco

* **MBR (Master Boot Record):** Utilizado para inicializar o computador.


* **Superbloco:** Contém parâmetros-chave do sistema de arquivos e é lido na inicialização.


* **i-nodes:** Estruturas de dados (uma por arquivo) que contêm todas as informações sobre o arquivo.



<img width="943" height="296" alt="image" src="https://github.com/user-attachments/assets/ad908b76-199a-483e-9713-76d10931e953" />


---

## 4. Principais Sistemas de Arquivos

Abaixo, uma tabela comparativa dos sistemas de arquivos mencionados:

| Sistema | Significado | Características Principais |
| --- | --- | --- |
| **BFS** | Be File System | Suporta atributos estendidos e indexação tipo banco de dados.|
| **EFS** | Encrypting File System | Armazenamento criptografado no NTFS via chave pública.|
| **ext2** | 2º Extended FS | Antigo padrão Linux; não possui *journaling*.|
| **ext3** | 3º Extended FS | Evolução do ext2 com adição de *journaling*.|
| **ext4** | 4º Extended FS | Suporta volumes de até 1 EiB e arquivos de 16 TiB.|
| **FAT** | File Allocation Table | Dividido em clusters; versões FAT12, 16 e 32.|
| **HFS+** | Hierarchical FS Plus | Desenvolvido pela Apple; utiliza estruturas B-tree.|
| **ISO 9660** | - | Padrão para CD-ROMs e DVDs.|
| **NTFS** | New Technology FS | Padrão Microsoft Windows; focado em recuperação e nomes longos.|
| **procfs** | Process FS | Pseudo sistema de arquivos (não ocupa disco) para informações do kernel.|
| **ZFS** | Zettabyte FS | Integra gerenciamento de volumes e verificação de integridade.|

---

## 5. Gerenciamento de Volumes Lógicos (LVM)

O **LVM (Logical Volume Manager)** resolve o problema de redimensionamento de partições sem a necessidade de interromper o servidor. Ele aloca discos físicos em **volumes lógicos** que podem ser expandidos facilmente.

* **Vantagens:** Redimensionamento flexível, utilização de discos paralelos e criação de *snapshots*.

* **Restrição Importante:** A partição `/boot/` geralmente não deve estar em um grupo de volume lógico porque o gestor de boot pode não conseguir acessá-la.



### Etapas para Configuração LVM

1. Criar o **Volume Físico (PV)** com `pvcreate`.


2. Criar o **Grupo de Volume (VG)** com `vgcreate`.


3. Criar o **Volume Lógico (LV)** com `lvcreate`.


4. Formatar e montar o volume (ex: `mkfs.ext4` e `mount`).

<img width="400" height="229" alt="image" src="https://github.com/user-attachments/assets/e9b52876-d090-42a2-8141-0a164aafef5a" />


---

## 6. Memória SWAP (Espaço de Troca)

A **SWAP** é uma parte do disco rígido utilizada como RAM virtual quando a memória física está cheia.

### Configuração de Arquivo SWAP no Linux

Para criar e ativar um arquivo de swap de 1GB:

```bash
# Criar o arquivo de 1GB
sudo fallocate -l 1G /swapfile

# Ajustar permissões
sudo chmod 600 /swapfile

# Formatar como swap e ativar
sudo mkswap /swapfile
sudo swapon /swapfile

# Verificar status
sudo swapon -s

```



Para tornar a alteração permanente, deve-se adicionar a seguinte linha ao arquivo `/etc/fstab`:


`/swapfile none swap sw 0 0`.

<img width="598" height="362" alt="image" src="https://github.com/user-attachments/assets/0785c521-4331-4f57-9d25-17c97019cd33" />


