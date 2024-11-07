FROM node:20-alpine

WORKDIR /app

# 빌드에 필요한 도구 설치 및 pnpm 설치
RUN npm install -g pnpm && pnpm install

# 애플리케이션 소스 코드 복사
COPY . .

# 빌드 실행
RUN pnpm build

# 애플리케이션이 실행될 포트 노출
EXPOSE 3000

# 애플리케이션 실행 명령어
CMD ["pnpm", "start:prod"]
