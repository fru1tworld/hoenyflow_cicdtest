FROM node:20-alpine

WORKDIR /app

RUN apk add --no-cache python3 make g++ && npm install -g pnpm

COPY package.json pnpm-lock.yaml ./

RUN pnpm install -r --frozen-lockfile

COPY . .

WORKDIR /app/packages/frontend

RUN pnpm --filter ./packages/frontend... build

EXPOSE 80
