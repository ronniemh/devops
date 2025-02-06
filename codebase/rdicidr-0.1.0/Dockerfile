FROM node:15.5.1 as builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx-debug", "-g", "daemon off;"]
