FROM php:8.4.2-fpm

COPY php.ini /usr/local/etc/php/

RUN apt update \
    && apt install -y default-mysql-client zlib1g-dev libzip-dev unzip \
    && docker-php-ext-install pdo_mysql zip

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update

RUN curl -sSL https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 -o mhsendmail && \
    chmod +x mhsendmail && \
    mv mhsendmail /usr/local/bin/mhsendmail

RUN apt-get -y update && apt-get -y install chromium libgconf-2-4

WORKDIR /var/www