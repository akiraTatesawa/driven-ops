FROM node:16 AS builder

WORKDIR /usr/src/

COPY package*.json ./
COPY prisma ./prisma/

RUN npm i

COPY . .

RUN npm config set cache /tmp --global

RUN npm run build

FROM node:16

COPY --from=builder /usr/src/node_modules ./node_modules
COPY --from=builder /usr/src/package*.json ./
COPY --from=builder /usr/src/dist ./dist
COPY --from=builder /usr/src/prisma ./prisma

EXPOSE 5000

CMD ["npm", "run", "start:migrate"]