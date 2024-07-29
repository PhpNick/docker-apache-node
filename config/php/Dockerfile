FROM composer
FROM php:8.2-apache

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update \
	&& apt-get install -y curl unzip python3-pip libzip-dev libpng-dev libwebp-dev libfreetype6-dev libjpeg62-turbo-dev && a2enmod rewrite ssl \
	&& docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp \ 
	&& docker-php-ext-install mysqli pdo pdo_mysql zip gd

RUN curl -fsSL https://deb.nodesource.com/setup_20.x -o nodesource_setup.sh
RUN bash nodesource_setup.sh
RUN apt-get install -y nodejs

USER www-data