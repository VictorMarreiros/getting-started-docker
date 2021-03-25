# Getting started with Docker
Following Docker [documentation example](https://docs.docker.com/get-started/02_our_app/)

### Clonar o repo dentro da pasta `/app`
> git clone https://github.com/VictorMarreiros/getting-started-docker.git app


### Building the App's Container Image
1. Criar um arquivo  `Dockerfile` dentro da mesma pasta que o arquivo `package.json` com o seguinte conteúdo:
```sh
FROM node:12-alpine
RUN apk add --no-cache python g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
```

2. Abra o terminal/cmd e vá até o diretório `app` com a `Dockerfile`. E agora crie a imagem do container usando o o comando `docker build`:
```sh
docker build -t getting-started .
```

### Starting an App Container
1. Start o container usando o comando `docker run` e especificando o nome da imagem que acabamos de criar:
```sh
docker run -dp 3000:3000 getting-started
```

2. Depois de algund segundos, abra o navegador web e vá para `http://localhost:3000`. Você deverá ver o app.

3. Vá em frente e adicione um ou dois itens e veja se o app funciona como esperado.