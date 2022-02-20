FROM golang:1.17-alpine

ENV CGO_ENABLED=0

# figlet: AAなど作成容易
# REF: https://pkgs.alpinelinux.org/package/v3.4/main/x86/figlet
RUN apk update && \
    apk upgrade && \
    apk add --update figlet

RUN go get -u github.com/cespare/reflex

# 環境によって異なるのでworkdirはcomposeで指定する
# WORKDIR /app/server
