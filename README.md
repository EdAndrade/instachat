<h1 align="center">
    Instachat
</h1>

<p align="center">
    O instachat é um web app que consiste em salas de chat particulares acessíveis com um código, são salas temporárias para trocas de mensagens em tempo real.
</p>

## :rocket: Tecnologias

* [NuxtJs (VueJs)](https://https://vuejs.org/)
* [Sass](https://sass-lang.com/)
* [Vuesax](https://vuesax.com/)
* [Vuex)](https://vuex.vuejs.org/)
* [Axios](https://axios-http.com/docs/intro)
* [Websockets](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
* [NodeJs](https://nodejs.org/en/about/)
* [ExpressJs](https://expressjs.com/)
* [MongoDB](https://www.mongodb.com/)
* [Docker](https://www.docker.com/)

## :computer: Como rodar

* Clone este repositório

```bash
$ git clone https://github.com/EdAndrade/instachat
```

* Clone o repositório do cliente e do servidor para dentro da pasta do projecto acima clonado (`instachat`)
```bash
$ git clone https://github.com/EdAndrade/instachat-client
$ git clone https://github.com/EdAndrade/instachat-api-v2
```

Nota: Neste README.md assume-se que você tenha o Docker e o docker-compose instalados na sua máquina, caso não tenha, acesse [este link](https://docs.docker.com/engine/install/) para saber sobre a instalação do docker, e [este link](https://docs.docker.com/compose/install/) para saber sobre a instalação do docker-compose

* Crie um arquivo `docker-compose.yml` e cole o código abaixo

```docker
version: '3.8'

services:
  frontend:
    build:
      context: ./instachat-client
    ports:
      - "4545:3000"
  backend:
    build:
      context: ./instachat-server
    ports:
      - "8085:8085"
      - "8081:8081"
  db:
    image: mongo
    volumes:
      - ./DB:/data/db
    environment:
      - MONGO_INITDB_ROOT_USERNAME=[USERNAME_DA_SUA_PREFERENCIA]
      - MONGO_INITDB_ROOT_PASSWORD=[PASSWORD_DA_SUA_PREFERENCIA]
    ports:
      - "27017:27017"
  db_adminer:
    image: mongoclient/mongoclient
    links:
      - "db:db"
    ports:
      - "9090:3000"
```

Notas: 
Certifique-se que as portas que serão usadas na sua maquina estão livres
Não esqueça de atribuir o username e a password nas variáveis de ambiente do serviço db

* Em seguida execute o seguinte comando para levantar todos serviços

```docker
docker-compose up -d --build
```

Assim que terminar, acesse apartir do browser http://localhost:4545/, enjoy it :smiley:

Obrigado! 💖