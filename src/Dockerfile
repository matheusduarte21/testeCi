FROM node:latest

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o package.json e o package-lock.json da pasta src
ADD ./src/package*.json ./

# Instalar as dependências
RUN npm install

# Copiar todo o conteúdo da pasta src para o diretório de trabalho no container
COPY ./src ./

# Comando para iniciar a aplicação
CMD [ "npm", "start" ]
