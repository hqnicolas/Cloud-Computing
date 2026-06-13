# Principais Comandos do Docker, Dockerfile, Docker Compose e Docker Swarm

Este documento apresenta uma referência rápida dos comandos mais comuns do Docker, Dockerfile, Docker Compose e Docker Swarm, organizados por categorias. Use este guia como um auxílio para gerenciar contêineres, imagens, serviços e orquestração.

## Docker - Geral

| Comando | Descrição |
| :--- | :--- |
| `docker version` | Exibe a versão do cliente e do servidor Docker. |
| `docker info` | Mostra informações sobre o sistema Docker, como número de contêineres e imagens. |
| `docker system df` | Exibe o uso de disco por imagens, contêineres e volumes. |
| `docker system prune` | Remove contêineres, redes e imagens não utilizados (use com cuidado). |

## Docker - Gerenciamento de Imagens

| Comando | Descrição |
| :--- | :--- |
| `docker images` | Lista todas as imagens disponíveis localmente. |
| `docker pull <imagem>[:tag]` | Baixa uma imagem do Docker Hub ou outro registro. Ex.: `docker pull nginx:latest`. |
| `docker build -t <nome>:<tag> .` | Constrói uma imagem a partir de um Dockerfile no diretório atual. |
| `docker rmi <imagem>` | Remove uma imagem específica. |
| `docker tag <origem> <destino>:<tag>` | Cria uma nova tag para uma imagem existente. |

## Docker - Gerenciamento de Contêineres

| Comando | Descrição |
| :--- | :--- |
| `docker run -d --name <nome> <imagem>` | Executa um contêiner em segundo plano com o nome especificado. Ex.: `docker run -d --name my-nginx nginx`. |
| `docker ps` | Lista os contêineres em execução. Use `-a` para incluir contêineres parados. |
| `docker stop <nome/id>` | Para um contêiner em execução. |
| `docker rm <nome/id>` | Remove um contêiner específico. |
| `docker logs <nome/id>` | Exibe os logs de um contêiner. Use `-f` para streaming contínuo. |
| `docker exec -it <nome/id> <comando>` | Executa um comando interativo em um contêiner. Ex.: `docker exec -it my-nginx bash`. |
| `docker port <nome/id>` | Lista as portas mapeadas de um contêiner. |

## Docker - Gerenciamento de Volumes e Redes

| Comando | Descrição |
| :--- | :--- |
| `docker volume ls` | Lista todos os volumes disponíveis. |
| `docker volume create <nome>` | Cria um novo volume. |
| `docker network ls` | Lista todas as redes disponíveis. |
| `docker network create <nome>` | Cria uma nova rede. Ex.: `docker network create my-network`. |
| `docker network connect <rede> <contêiner>` | Conecta um contêiner a uma rede específica. |

## Dockerfile - Comandos Principais

| Comando | Descrição |
| :--- | :--- |
| `FROM <imagem>[:tag]` | Define a imagem base para o build. Ex.: `FROM ubuntu:20.04`. |
| `RUN <comando>` | Executa um comando durante o build da imagem e commita o resultado. Ex.: `RUN apt-get update`. |
| `COPY <origem> <destino>` | Copia arquivos ou diretórios do host para a imagem. Ex.: `COPY . /app`. |
| `ADD <origem> <destino>` | Similar ao COPY, mas também suporta URLs e descompactação de arquivos. |
| `WORKDIR <diretório>` | Define o diretório de trabalho para comandos subsequentes. Ex.: `WORKDIR /app`. |
| `EXPOSE <porta>` | Indica que a imagem escuta em uma porta específica. Ex.: `EXPOSE 80`. |
| `CMD ["comando", "arg1"]` | Define o comando padrão a ser executado quando o contêiner inicia. Pode ser sobrescrito. |
| `ENTRYPOINT ["comando"]` | Define o comando principal do contêiner, que não é sobrescrito facilmente. |

## Docker Compose - Comandos Principais

| Comando | Descrição |
| :--- | :--- |
| `docker-compose up` | Inicia todos os serviços definidos no arquivo `docker-compose.yml`. Use `-d` para rodar em segundo plano. |
| `docker-compose down` | Para e remove os contêineres, redes e volumes criados pelo `up`. |
| `docker-compose ps` | Lista os contêineres gerenciados pelo Compose no projeto atual. |
| `docker-compose build` | Constrói ou reconstrói as imagens definidas no `docker-compose.yml`. |
| `docker-compose logs` | Exibe os logs de todos os serviços. Use `-f` para streaming contínuo. |
| `docker-compose exec <serviço> <comando>` | Executa um comando em um serviço. Ex.: `docker-compose exec web bash`. |
| `docker-compose restart` | Reinicia todos os serviços. |

## Docker Swarm - Comandos Principais

| Comando | Descrição |
| :--- | :--- |
| `docker swarm init` | Inicializa um novo cluster Swarm no nó atual. |
| `docker swarm join <token>:<ip>:<porta>` | Conecta um nó ao cluster Swarm existente. |
| `docker node ls` | Lista todos os nós no cluster Swarm. |
| `docker service create --name <nome> <imagem>` | Cria um serviço no Swarm. Ex.: `docker service create --name my-app nginx`. |
| `docker service ls` | Lista todos os serviços no cluster Swarm. |
| `docker service scale <nome>=<réplicas>` | Ajusta o número de réplicas de um serviço. Ex.: `docker service scale my-app=3`. |
| `docker service ps <nome>` | Mostra as tarefas (contêineres) de um serviço específico. |
| `docker service rm <nome>` | Remove um serviço do cluster Swarm. |

---
*Nota: Use a opção `--help` com qualquer comando para obter mais detalhes. Para mais informações, consulte a documentação oficial do Docker ou a documentação do Docker Swarm.*