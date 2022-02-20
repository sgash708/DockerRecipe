FROM ubuntu:latest

ENV LANG=jpn

RUN apt update \
    && apt install -y \
    wget curl unzip make libxkbcommon0 libatspi2.0-0 libgbm1 tzdata \
    ca-certificates \
    libtesseract-dev \
    tesseract-ocr \
    tesseract-ocr-$LANG \
    software-properties-common \
    libfontconfig \
    && mkdir -p /home/root/src \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add \
    && echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list \
    && apt update -qq \
    && apt install -y google-chrome-stable libnss3 libgconf-2-4

RUN CHROMEDRIVER_VERSION=`curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE` \
    && curl -sS -o /tmp/chromedriver_linux64.zip http://chromedriver.storage.googleapis.com/$CHROMEDRIVER_VERSION/chromedriver_linux64.zip \
    && unzip /tmp/chromedriver_linux64.zip \
    && mv chromedriver /usr/local/bin/

RUN add-apt-repository ppa:longsleep/golang-backports \
    && apt install -y golang

ENV TZ=Asia/Tokyo

ENV GO111MODULE=on
ENV GOPATH=$HOME/go
ENV PATH=$PATH:$GOPATH/bin
