# 以下に欲しいバージョンを記入
#　詳細はこちらhttps://hub.docker.com/_/php
FROM php:7.3-apache
RUN apt-get update  \
  && docker-php-ext-install pdo_mysql mysqli mbstring \
  && a2enmod rewrite

WORKDIR /var/www/html

EXPOSE 80