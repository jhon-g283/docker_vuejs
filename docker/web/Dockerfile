FROM node:14.15.0-alpine

WORKDIR /app

EXPOSE 8080

RUN apk update && \
    npm install && \
    npm install -g npm && \
    npm install -g vue-cli
# 初回コマンドらしい、docker-compose up でnpm startを実行し初期表示させたい時書く必要がある。ビルドも必須、ビルドしたらnpm startを認識するようになるイメージ
CMD [ "npm", "start"]