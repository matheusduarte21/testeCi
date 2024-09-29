# Stage 1 - Build React app
FROM node:20

# Define o diretório de trabalho no container
WORKDIR /app

# Copia os arquivos de dependências
COPY package.json package-lock.json ./ 

# Instala as dependências
RUN npm install

# Copia o diretório 'public' e os arquivos de código fonte da aplicação
COPY . .

# Gera o build da aplicação React
RUN npm run build

# Stage 2 - Configurar Nginx para servir a aplicação
FROM nginx:alpine

# Copia o build da aplicação para o diretório de arquivos estáticos do Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Expor a porta 80 para servir a aplicação
EXPOSE 80

# Comando para rodar o Nginx no container
CMD ["nginx", "-g", "daemon off;"]
