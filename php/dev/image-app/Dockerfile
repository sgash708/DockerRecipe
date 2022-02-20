FROM sugar708/lara708:php-8

# LaravelMixでコンパイルしたいのでCI/CDで実行
# envの前に実行するとよし
RUN npm ci
RUN npm run prod

#COPY ../server /var/www/html
#COPY ../env.example /var/www/html/.env
