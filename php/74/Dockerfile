FROM php:7.4.21

WORKDIR /var/www

# development / production
ARG PHP_ENV=development

# development / production
RUN apt-get update \
    && apt-get install -y vim \
    && apt-get install -y git \
    && curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ \
    && apt-get install -y libwebp-dev libjpeg-dev libpng-dev libfreetype6-dev \
    && cp /usr/local/etc/php/php.ini-$PHP_ENV /usr/local/etc/php/php.ini \
    && docker-php-ext-install php-cli php-common bcmath pdo_mysql gd \
    && pecl install redis \
    && docker-php-ext-enable redis
