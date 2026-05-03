# Docker

### Conceitos Fundamentais
*   **Container**
    *   Empacota o código da aplicação junto com todas as dependências, garantindo que o software rode da mesma forma em qualquer computador.
*   **Image (Imagem)**
    *   É um "snapshot" (foto) estático do seu projeto. É a planta da construção que o Docker usa para criar os containers.
*   **Docker File**
    *   Arquivo de texto que contém as instruções passo a passo para gerar uma imagem do Docker automaticamente.
*   **Environments (Variáveis de Ambiente)**
    *   Configura as variáveis de ambiente dos containers (como senhas de banco de dados e chaves de API) sem precisar mexer no código.
*   **Volumes**
    *   Forma de persistir dados. Como o container é temporário, o Volume serve para salvar os arquivos do banco de dados ou o seu código fonte para que eles não sumam ao desligar o container.
*   **Docker Compose**
    *   Ferramenta para definir e rodar aplicações de múltiplos containers (ex: um container para o PHP e outro para o MySQL) usando um único arquivo `.yml`.

---

### Comandos de Gerenciamento
*   **docker ps**
    *   Lista todos os containers que estão rodando no momento.
*   **docker ps -a**
    *   Lista todos os containers do sistema, inclusive os que estão parados ou foram utilizados anteriormente.
*   **docker stop ID_DO_CONTAINER**
    *   Para todos os processos dentro de um container específico de forma segura.
*   **docker start ID_DO_CONTAINER**
    *   Inicia um container que já existe mas estava parado.
*   **docker rm ID_DO_CONTAINER**
    *   Remove um container permanentemente (ele precisa estar parado antes).
*   **docker images**
    *   Lista todas as imagens que você baixou ou buildou no seu computador.
*   **docker build -t NOME_DA_IMAGEM:VERSAO .**
    *   Cria a imagem, o ponto final é importante pro dockerfile saber que está na root
*   **docker run NOME_DA_IMAGEM:VERSAO**
    *   Cria a imagem, o ponto final é importante pro dockerfile saber que está na root
---

### Interação e Desenvolvimento
*   **docker exec -it ID_DO_CONTAINER bash**
    *   Abre um terminal dentro do container para que você possa navegar nos arquivos como se estivesse em uma máquina Linux separada.
*   **docker logs -f ID_DO_CONTAINER**
    *   Mostra em tempo real o que está acontecendo "dentro" do container (útil para ver erros de código no Laravel ou Node).
*   **docker system prune**
    *   Limpa containers parados, redes não utilizadas e imagens sem nome. Ótimo para liberar espaço no HD.
