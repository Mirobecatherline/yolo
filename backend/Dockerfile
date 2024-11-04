FROM node:14 AS build

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

FROM alpine:3.16.7

# Install both nodejs and npm
RUN apk update && apk add --update nodejs npm

WORKDIR /app

COPY --from=build /usr/src/app /app

EXPOSE 5000

CMD ["node", "server.js"]
