FROM node:lts-alpine

# FIX: bootstrapのインストールごけを修正
# REF: https://qiita.com/hym816/items/a40bd66395f17b78344b
RUN apk update && \
    apk add git

WORKDIR /app
