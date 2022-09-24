# Multi Step Dockerfile

#phase 1 - build container
FROM node:16-alpine as builder
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build

#phase 2 - copy phase 1 build folder into nginx container
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
