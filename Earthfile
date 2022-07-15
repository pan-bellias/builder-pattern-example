FROM node:12.13.0-alpine as build
WORKDIR /app

build:
  COPY package*.json ./
  RUN npm install
  COPY . .
  RUN npm run build

final:
  FROM nginx
  EXPOSE 3000
  COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
  COPY  +build/app/build /usr/share/nginx/html