FROM node:16

WORKDIR /app

COPY . .

RUN export NODE_OPTIONS="--max-old-space-size=8192"

RUN npm i && npm run build

RUN mkdir -p /var/www/html

RUN mv build/* /var/www/html

WORKDIR /

RUN rm -rf /app