FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
    libmcrypt-dev \
    mysql-client \
    libmemcached-dev \
    libz-dev \
    libxml2 libxml2-dev\
    && docker-php-ext-install pdo_mysql mbstring xml

RUN pecl install mcrypt-1.0.1 \
    && pecl install xdebug-2.6.0 \
    && pecl install memcached-3.0.0 \
    && docker-php-ext-enable mcrypt xdebug memcached

EXPOSE 9000