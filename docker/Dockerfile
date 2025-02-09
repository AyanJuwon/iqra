FROM php:8.2-fpm

# Install system dependencies and libraries for GD and others.
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install PHP extensions:
# - pdo_mysql and mbstring for Laravel
# - GD with FreeType and JPEG support
RUN docker-php-ext-install pdo_mysql mbstring

RUN docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install gd

# The sodium extension is bundled with PHP 8.2 but if needed you can ensure it is enabled:
# RUN docker-php-ext-install sodium

# Install dependencies
RUN apt update && apt install -y curl unzip git

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer

# Set working directory
WORKDIR /var/www/html
