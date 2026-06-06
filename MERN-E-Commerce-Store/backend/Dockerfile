FROM node:18-alpine

WORKDIR /app

COPY MERN-E-Commerce-Store/package*.json ./
RUN npm install

COPY MERN-E-Commerce-Store/backend ./

EXPOSE 5000

CMD ["node", "index.js"]