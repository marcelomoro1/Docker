# Controle de Versão e Rollback no Docker Compose

Este documento orienta como configurar e utilizar o sistema de **Tags** no `docker-compose.yml`. Essa estratégia permite criar versões numeradas do sistema e realizar o **Rollback (retorno ao passado)** em segundos caso uma atualização apresente problemas em produção.

---

## Configuração no `docker-compose.yml`

Adicione a propriedade `image` com a variável `${TAG:-latest}` logo abaixo do nome de cada um dos contêineres/serviços.

### Exemplo:
```yaml
services:
  backend-teste:
    image: cofelma-backend:${TAG:-latest}
    build:
      context: ./backend_manutencao
    # ... resto das configurações ...

  frontend-teste:
    image: cofelma-frontend:${TAG:-latest}
    build:
      context: ./frontend_manutencao
    # ... resto das configurações ...

```

## Agora com o Docker Compose configurado
Ao invés de subir os containers normalmente com o `docker compose up -d --build`
Você sobe os containers com `TAG=v1.0.1 docker compose up -d --build`
Apenas alterando a versão que vai conter a imagem dos dois containers.

## COMO VOLTAR A VERSÃO?
Caso voce tenha feito um build `TAG=v1.0.2 docker compose up -d --build`
E essa v1.0.2 deu problema apenas use o comando:

`TAG=v1.0.1 docker compose up -d`

Por que esse comando vai voltar para a versão anterior que já foi buildada e que está funcionado, então não pode usar o build nele pra não sobreescrever a versão

