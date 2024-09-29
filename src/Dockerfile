# syntax=docker/dockerfile:1.4
# 1. For build React app
FROM node:lts AS development

# Set working directory
WORKDIR /app

# Copiar o package.json e package-lock.json para o diretório de trabalho
COPY package.json package-lock.json ./

# Instalar dependências
RUN npm ci

# Copiar todo o conteúdo da pasta src para o diretório /app
COPY . ./

ENV CI=true
ENV PORT=3000

CMD ["npm", "start"]

# Build stage
FROM development AS build

RUN npm run build

# Development environment
FROM development AS dev-envs
RUN apt-get update && apt-get install -y --no-install-recommends git

# Adiciona usuário vscode e grupo docker
RUN useradd -s /bin/bash -m vscode && \
    groupadd docker && \
    usermod -aG docker vscode

# 2. For Nginx setup
FROM nginx:alpine

# Copiar configuração do nginx
COPY --from=build /app/.nginx/nginx.conf /etc/nginx/conf.d/default.conf

WORKDIR /usr/share/nginx/html

# Remove assets estáticos padrão do nginx
RUN rm -rf ./*

# Copiar assets estáticos do estágio de build
COPY --from=build /app/build ./

# Containers run nginx with global directives and daemon off
ENTRYPOINT ["nginx", "-g", "daemon off;"]
