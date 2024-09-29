# syntax=docker/dockerfile:1.4
# 1. For build React app
FROM node:lts AS development

# Set working directory
WORKDIR /app

# Copiar o package.json e package-lock.json para o diretório de trabalho
COPY ./src/package.json ./src/package-lock.json ./

# Instalar dependências
RUN npm ci

# Copiar todo o conteúdo da pasta src para o diretório /app
COPY ./src ./

# Definir variáveis de ambiente
ENV CI=true
ENV PORT=3000

# Rodar o build
RUN npm run build

# Executar a aplicação
CMD ["npm", "start"]
