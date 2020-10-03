FROM php:8.0.0rc1-fpm-buster
WORKDIR /usr/src/PHP-CS-Fixer
RUN apt-get update && apt-get install -y \
        libzip-dev \
        unzip \
        wget \
        zip \
    && docker-php-ext-install -j$(nproc) zip
COPY install-composer.sh .
RUN ./install-composer.sh
