FROM node:18-alpine

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories && \
    apk update && \
    apk add --no-cache docker-cli docker-cli-compose && \
    npm config set registry http://registry.npm.taobao.org

WORKDIR /letsencrypt-docker-compose/cli
COPY package*.json ./
RUN npm ci --only=production
COPY . .
ENV NODE_ENV=production

WORKDIR /workdir

CMD ["node", "/letsencrypt-docker-compose/cli/src/app.js"]