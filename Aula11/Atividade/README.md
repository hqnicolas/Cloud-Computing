# Atividades Práticas de Docker

Este documento apresenta um conjunto de 5 questões práticas focadas no uso de Docker, abrangendo desde a execução básica de contêineres até a persistência de dados e automação com Dockerfile.

---

### Questão 1: Criar e executar um contêiner Nginx
**Objetivo:** Aprender a baixar uma imagem do Docker Hub e executar um contêiner simples com o servidor web Nginx.
**Tipo:** Envio de arquivo (PDF com comandos e capturas de tela)

**Passos:**
1. Baixe a imagem oficial do Nginx do Docker Hub.
2. Execute um contêiner a partir dessa imagem, mapeando a porta 80 do contêiner para a porta 8080 do host.
3. Acesse o servidor Nginx no navegador (`http://localhost:8080`) para verificar se está funcionando.

---

### Questão 2: Criar um contêiner com uma aplicação Python simples
**Objetivo:** Criar um Dockerfile para executar um script Python simples em um contêiner.
**Tipo:** Envio de arquivo (PDF com comandos e capturas de tela)

**Passos:**
1. Crie um arquivo Python com um comando `print()` simples.
2. Crie um `Dockerfile` para configurar a imagem baseada em Python.
3. Construa a imagem e execute o contêiner.

---

### Questão 3: Gerenciar contêineres (iniciar, parar e remover)
**Objetivo:** Praticar comandos de gerenciamento de contêineres.
**Tipo:** Envio de arquivo (PDF com comandos e capturas de tela)

**Passos:**
1. Crie um contêiner com a imagem `alpine` (uma distribuição Linux leve).
2. Execute comandos para iniciar, parar e remover o contêiner.
3. Liste os contêineres (ativos e inativos) para verificar o estado.

---

### Questão 4: Persistir dados com volumes
**Objetivo:** Entender como usar volumes para persistir dados entre execuções de contêineres.
**Tipo:** Envio de arquivo (PDF com comandos e capturas de tela)

**Passos:**
1. Crie um contêiner com a imagem `nginx`.
2. Monte um volume (bind mount ou volume gerenciado) para persistir arquivos HTML.
3. Modifique um arquivo no volume e verifique a persistência dos dados após reiniciar o contêiner.

---

### Questão 5: Executar um contêiner com uma aplicação Node.js
**Objetivo:** Criar uma aplicação Node.js simples e executá-la em um contêiner Docker.
**Tipo:** Envio de arquivo (PDF com comandos e capturas de tela)

**Passos:**
1. Crie um arquivo JavaScript com um servidor HTTP simples.
2. Crie um `Dockerfile` para a aplicação.
3. Construa a imagem e execute o contêiner mapeando as portas necessárias.