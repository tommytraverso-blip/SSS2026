# Prima fase: costruzione dell'applicazione Angular
FROM node:24-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

# Seconda fase: server web Nginx
FROM nginx:alpine

COPY --from=build /app/dist/SomeBankingFrontend/browser /usr/share/nginx/html

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80