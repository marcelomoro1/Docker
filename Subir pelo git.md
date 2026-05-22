# Subindo os containers do GitHub


* Se conectar via terminal SSH -> ssh root@ip

* cd até a pasta onde está o seu docker -> cd /var/www/html/docker-manutencao

* cd até o repositorio -> cd /var/www/html/docker-manutencao/backend_manutencao

* git init

* git pull origin main

* git pull origin main NÃO deu certo? -> git fetch origin | git reset --hard origin/main

* cd de volta para a pasta raiz do projeto -> cd /var/www/html/docker-manutencao

* cd até a pasta do frontend e faça o mesmo

* cd até a pasta raiz do projeto com o docker-compose

* builde os containers da aplicação -> docker compose up -d --build

* Verificar se os containers subiram -> docker compose ps

