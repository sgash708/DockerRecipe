FROM php:8.0-apache

# 設定ファイル
COPY php.ini /usr/local/etc/php/conf.d
COPY 000-default.conf /etc/apache2/sites-available/
COPY alias.conf /etc/apache2/mods-enabled/alias.conf

# Headersモジュールの有効化
RUN /bin/sh -c 'a2enmod headers'
COPY security.conf /etc/apache2/conf-enabled/security.conf

# intl Laravelバリデータ
RUN apt-get update \
    && apt-get install -y vim zlib1g-dev libzip-dev mariadb-client libicu-dev unzip \
    && docker-php-ext-configure intl \
    && docker-php-ext-install zip pdo_mysql mysqli opcache intl

# nodeJSをインストール
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs

# composerをインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

# LaravelのmodRewriteを有効化
RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite

# 作業環境
WORKDIR /var/www/html

# laravelをインストール
RUN composer global require "laravel/installer"
