FROM node:19
WORKDIR /frontend
ADD package*.json ./
COPY . .
RUN npm install
CMD [ "npm", "start" ]