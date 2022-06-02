FROM rust:1.52.1

ENV CARGO_TARGET_DIR=/tmp/target \
  DEBIAN_FRONTEND=noninteractive \
  LC_CTYPE=ja_JP.utf8 \
  LANG=ja_JP.utf8

RUN apt-get update \
  && apt-get upgrade -y \
  && apt-get install -y -q \
  ca-certificates \
  locales \
  apt-transport-https\
  libssl-dev \
  libpq-dev \
  pkg-config \
  curl \
  build-essential \
  libdbus-1-dev \
  libsqlite3-dev \
  mariadb-client \
  git \
  wget \
  && echo "ja_JP UTF-8" > /etc/locale.gen \
  && locale-gen \
  && echo "install rust tools" \
  && rustup component add rustfmt \
  && cargo install cargo-watch cargo-make \
  && cargo install sqlx-cli --no-default-features --features mysql

WORKDIR /var/rust
