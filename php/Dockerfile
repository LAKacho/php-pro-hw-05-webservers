FROM php:8.3-fpm-alpine

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && apk del $PHPIZE_DEPS

COPY php.ini /usr/local/etc/php/conf.d/sessions.ini
WORKDIR /var/www
