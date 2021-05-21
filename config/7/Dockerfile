FROM php:7.4-fpm

RUN apt-get update && apt-get install -y libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*
RUN printf "\n" | pecl install imagick

# Install PHP extensions
RUN docker-php-ext-enable imagick
RUN docker-php-ext-install mysqli pdo pdo_mysql

#RUN pecl install xdebug-2.9.5 && docker-php-ext-enable xdebug

# Install system dependencies
RUN apt-get update && apt-get install -y git

RUN pecl install xdebug-3.0.0 && docker-php-ext-enable xdebug

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer


# Set working directory
WORKDIR /var/www
