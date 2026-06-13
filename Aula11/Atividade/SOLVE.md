# Resolução: Atividades Práticas de Docker

Este documento contém os comandos, códigos e o passo a passo para resolver as 5 questões práticas de Docker.

---

## Questão 1: Criar e executar um contêiner Nginx

**1. Baixar a imagem oficial do Nginx:**
```bash
docker pull nginx

```

**2. Executar o contêiner mapeando a porta 8080 (host) para 80 (contêiner):**

```bash
docker run -d -p 8080:80 --name meu-nginx nginx

```

*(A flag `-d` roda o contêiner em segundo plano).*

**3. Testar no navegador ou terminal:**
Acesse `http://localhost:8080` no seu navegador ou execute no terminal:

```bash
curl http://localhost:8080

```

---

## Questão 2: Criar um contêiner com uma aplicação Python simples

**1. Criar o arquivo Python (`app.py`):**
Crie um arquivo chamado `app.py` e adicione o seguinte código:

```python
print("Olá! Este script Python está rodando dentro de um contêiner Docker.")

```

**2. Criar o `Dockerfile`:**
No mesmo diretório, crie um arquivo chamado `Dockerfile` (sem extensão) com o seguinte conteúdo:

```dockerfile
# Usar a imagem oficial do Python
FROM python:3.9-slim

# Definir o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copiar o script local para o contêiner
COPY app.py .

# Comando para executar o script
CMD ["python", "app.py"]

```

**3. Construir a imagem e executar o contêiner:**

```bash
# Construir a imagem (não esqueça o ponto final)
docker build -t minha-app-python .

# Executar o contêiner
docker run --name cont-python minha-app-python

```

---

## Questão 3: Gerenciar contêineres (iniciar, parar e remover)

**1. Criar e rodar um contêiner com a imagem `alpine` em segundo plano:**

```bash
docker run -d --name meu-alpine alpine sleep 1000

```

*(O comando `sleep 1000` mantém o contêiner ativo para podermos gerenciá-lo).*

**2. Listar contêineres ativos:**

```bash
docker ps

```

**3. Parar o contêiner:**

```bash
docker stop meu-alpine

```

**4. Listar todos os contêineres (ativos e inativos) para checar o status "Exited":**

```bash
docker ps -a

```

**5. Iniciar novamente o contêiner e depois removê-lo:**

```bash
docker start meu-alpine
docker stop meu-alpine
docker rm meu-alpine

```

*(Dica: Para remover um contêiner que está rodando, você pode forçar com `docker rm -f meu-alpine`).*

---

## Questão 4: Persistir dados com volumes

Para este exemplo, usaremos um **Bind Mount** (mapear uma pasta local para dentro do contêiner).

**1. Criar um arquivo HTML localmente:**
Crie uma pasta chamada `site_local` e dentro dela um arquivo `index.html`:

```html
<h1>Página persistida via Docker Volume!</h1>

```

**2. Executar o Nginx montando o volume:**
Execute o comando abaixo estando no diretório onde a pasta `site_local` foi criada:

```bash
# No Linux/Mac:
docker run -d -p 8080:80 -v $(pwd)/site_local:/usr/share/nginx/html --name nginx-volume nginx

# No Windows (PowerShell):
docker run -d -p 8080:80 -v ${PWD}\site_local:/usr/share/nginx/html --name nginx-volume nginx

```

**3. Testar a persistência:**

* Acesse `http://localhost:8080` (você verá sua página customizada).
* Modifique o arquivo `index.html` localmente.
* Recarregue a página no navegador. A alteração refletirá imediatamente, provando que os dados estão persistidos e linkados entre o Host e o Contêiner.

---

## Questão 5: Executar um contêiner com uma aplicação Node.js

**1. Criar a aplicação Node.js (`server.js`):**
Crie um arquivo chamado `server.js` com um servidor HTTP básico:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Ola, Node.js rodando no Docker!\n');
});

server.listen(3000, () => {
  console.log('Servidor rodando na porta 3000...');
});

```

**2. Criar o `Dockerfile`:**
Crie o arquivo `Dockerfile` na mesma pasta:

```dockerfile
# Imagem base
FROM node:18-alpine

# Diretório de trabalho
WORKDIR /usr/src/app

# Copiar os arquivos
COPY server.js .

# Expor a porta 3000
EXPOSE 3000

# Comando para iniciar a aplicação
CMD ["node", "server.js"]

```

**3. Construir a imagem e executar o contêiner:**

```bash
# Fazer o build da imagem
docker build -t meu-node-app .

# Rodar mapeando a porta 3000
docker run -d -p 3000:3000 --name node-container meu-node-app

```

**4. Testar a aplicação:**
Acesse `http://localhost:3000` no navegador.

```