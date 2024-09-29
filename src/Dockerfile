FROM node:latest
WORKDIR /app
ADD package*.json ./
RUN npm install
COPY . .
CMD [ "npm", "start" ]