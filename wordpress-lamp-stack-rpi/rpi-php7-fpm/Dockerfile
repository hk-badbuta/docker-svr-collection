FROM php:7.4-fpm-buster

MAINTAINER BadBUTA <badbuta@hotmail.com>
LABEL Vendor="badbuta"
LABEL Description="PHP-FPM 7 for wordpress website"
LABEL Version="v1.0"

# install PHP extensions & PECL modules with dependencies
RUN apt-get update && apt-get install -y \
    mc \
    vim \
    wget \
    curl

RUN apt-get install -y \
    libicu-dev \
    libpq-dev \
    libbz2-dev \
    libzip-dev \
    libonig-dev \
    libevent-dev \
    libxml2 \
    libxslt-dev \
    && docker-php-ext-install xsl \
    && docker-php-ext-install iconv \
    && docker-php-ext-install zip \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install intl \
    # && docker-php-ext-install pgsql pdo pdo_pgsql \
    && docker-php-ext-install pdo_mysql mysqli \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install opcache \
    && docker-php-ext-enable opcache

RUN apt-get install -y -q --no-install-recommends \
    msmtp

# Install mcrypt
RUN apt-get install -y libmcrypt-dev \
    && yes | pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt

# Install GD
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd \
	--with-freetype \
	--with-jpeg \
    && docker-php-ext-install gd \
    && docker-php-ext-enable gd

# Install Imagick
RUN apt-get install -y \
        libmagickwand-dev \
    && yes | pecl install imagick \
    && docker-php-ext-enable imagick

# Install EXIF
RUN docker-php-ext-install exif \
    && docker-php-ext-enable exif

# Finallly
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/*
