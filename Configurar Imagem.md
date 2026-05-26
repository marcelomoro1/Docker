Adicionar um em cada um dos containers no Docker-compose.yaml

image: cofelma-backend:${TAG:-latest}
image: cofelma-frontend:${TAG:-latest}

Exemplo:
services:
  backend-teste:
    image: cofelma-backend:${TAG:-latest}
    build:
      context: ...


Agora com o docker-compose configurado
Ao invés de subir os containers normalmente com o "docker compose up -d --build"
Você sobe os containers com TAG=v1.0.1 docker compose up -d --build
Apenas alterando a versão que vai conter a imagem dos dois containers

COMO VOLTAR A VERSÃO?
Caso voce tenha feito um build TAG=v1.0.2 docker compose up -d --build
E essa v1.0.2 deu problema apenas use o comando:
TAG=v1.0.1 docker compose up -d --build

Por que esse comando vai voltar para a versão anterior que já foi buildade e que está correta.

