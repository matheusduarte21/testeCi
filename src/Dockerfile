FROM node:19.5.0-alpine
WORKDIR /frontend
ADD package*.json ./
COPY . .
RUN npm install
CMD [ "npm", "start" ]