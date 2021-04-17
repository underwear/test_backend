FROM php:7.4-fpm-buster

RUN apt-get update \
    && apt-get install -y --no-install-recommends wkhtmltopdf libmcrypt-dev libpq-dev libzip-dev zlib1g-dev libxml2-dev cpio

RUN docker-php-source extract \
    && docker-php-ext-install bcmath pdo_pgsql pdo_mysql soap sockets zip \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && docker-php-source delete

WORKDIR /opt/project

RUN apt-get update \
    && apt-get install --no-install-recommends -y unzip git

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/bin --filename=composer \
    && rm composer-setup.php