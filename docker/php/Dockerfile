FROM php:8.2.0-fpm

RUN apt-get update && apt-get install -y \
        cron \
        git \
        libzip-dev \
        zip \
        unzip \
        libpq-dev \
        libwebp-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libfreetype6-dev \
        libicu-dev \
    && docker-php-ext-configure gd --with-webp --with-jpeg --with-freetype \
    && docker-php-ext-configure intl \
    && docker-php-ext-install zip bcmath gd mysqli pdo_mysql intl pdo_pgsql

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# RUN apt-get install -y supervisor && pecl install -o -f redis && rm -rf /tmp/pear && docker-php-ext-enable redis

RUN docker-php-ext-install sockets

WORKDIR /var/www/html

COPY cron-file /etc/cron.d/cron-file
COPY run-daemons.sh /run-daemons.sh

RUN chmod +x /run-deamons.sh

ENTRYPOINT /bin/bash /run-daemons.sh
