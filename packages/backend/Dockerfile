FROM node:20-alpine

WORKDIR /app

# 빌드에 필요한 도구 설치 및 pnpm 설치
RUN apk add --no-cache python3 make g++ \
    && npm install -g pnpm

# 루트의 package.json 및 pnpm-lock.yaml 복사 및 종속성 설치
COPY package.json pnpm-lock.yaml ./
RUN pnpm install -r --frozen-lockfile

# backend 소스 코드 복사 및 backend 작업 디렉터리 설정
COPY packages/backend /app/packages/backend

# backend 디렉터리로 이동
WORKDIR /app/packages/backend

# NestJS 빌드 (TypeScript 컴파일)
RUN pnpm build

# 애플리케이션이 실행될 포트 노출
EXPOSE 3000

# 실행 명령어 - 빌드 결과를 실행
CMD ["node", "dist/main"]
