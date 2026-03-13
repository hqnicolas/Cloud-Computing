# Aula 03: Sistemas de Arquivos e Gerenciamento de Swap

---

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

*   **Arquivo:** Definido como uma sequência de bytes com uma estrutura interna específica e atributos como tamanho, datas de acesso e proprietário.
*   **Diretório:** Um arquivo especial que mapeia nomes para identificadores, podendo conter subdiretórios em uma estrutura de árvore.

---

## 3. Exemplo Prático: Gerenciamento de Swap

Um exemplo de gerenciamento de espaço persistente é a criação e ativação de um arquivo de swap, que permite ao sistema operacional usar espaço em disco como memória RAM adicional.

Para criar e ativar um arquivo de swap:

```bash
sudo mkswap /swapfile
sudo swapon /swapfile

# Verificar status
sudo swapon -s
```

Para tornar a alteração permanente, adicione a seguinte linha ao arquivo `/etc/fstab`:

```
/swapfile none swap sw 0 0
```