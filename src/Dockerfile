FROM node:latest

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o package.json e o package-lock.json da pasta src
ADD package*.json ./

# Instalar as dependências
RUN npm install

# Copiar todo o conteúdo da pasta atual (src) para o diretório de trabalho no container
COPY . .

# Comando para iniciar a aplicação
CMD [ "npm", "start" ]
