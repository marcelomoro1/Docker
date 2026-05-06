# Deploy: Frontend & Backend com Docker e Portainer

### 1. Dockerização da Aplicação
Criar um dockerfile para o backend e para o frontend
Os Dockerfiles são responsáveis por criar as imagens base da aplicação.

* **Backend:** Instala as dependências e prepara o ambiente da API.
* **Frontend:** Gera os arquivos estáticos (build) e utiliza o **Apache** para servir a aplicação.

---

### 2. Build e Push de Imagens

O processo de atualização consiste em gerar uma nova imagem com tag de versão e enviá-la para o registry.

```bash
# Buildar a imagem
docker build -t seu-usuario/nome-da-app:v1.0 .

# Enviar para o registry
docker push seu-usuario/nome-da-app:v1.0

Para o deploy no Portainer, basta avisar ao orquestrador para usar a nova versão da imagem.
```
### 3. Configurando o Portainer (Stack)

No Portainer, adicione uma nova Stack e utilize o editor para configurar o compose.yml. Este arquivo define como o front e o back se comportam:## 2. Build e Push de Imagens
```
services:
  frontend:
    image: seu-usuario/react-app:v1.0  # Sempre use tags de versão, evite a 'latest'
    ports:
      - "8080:80"   # O Apache vai olhar para essa porta 8080
    restart: always

  backend:
    image: seu-usuario/api-backend:v1.0
    ports:
      - "3000:3000" # O Apache vai olhar para essa porta 3000
    environment:
      - DATABASE_URL=mongodb://mongo:27017/minhadb
    restart: Always
```
### 4. Configuração do Servidor
No servidor host, configure o Proxy Pass para apontar o tráfego de entrada para as portas específicas do Docker:
```
Tráfego Web -> Porta 8080 (Frontend)

Tráfego API -> Porta 3000 (Backend)
```
### 5. Dando Rollback

Vá na Stack correspondente no Portainer.

Altere a tag da imagem no editor (ex: de v1.1 para v1.0).

Clique em Update the stack



