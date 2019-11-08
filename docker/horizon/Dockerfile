FROM php:7.3-alpine

RUN apk --update add postgresql-dev \
    libpng-dev \
    freetype-dev \
    libjpeg-turbo-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pcntl \
    && docker-php-ext-install pdo_pgsql

RUN php -v | head -n 1 | grep -q "PHP 7.3."

CMD ["php", "artisan", "horizon"]

WORKDIR /var/www/laravel