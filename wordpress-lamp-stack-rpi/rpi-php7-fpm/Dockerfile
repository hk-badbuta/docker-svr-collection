FROM shaula/rpi-php7-fpm

MAINTAINER BadBUTA <badbuta@gmail.com>
LABEL Vendor="badbuta"
LABEL Description="PHP-FPM 7 for badbuta.com website"
LABEL Version="v1.0"

# install PHP extensions & PECL modules with dependencies
RUN apt-get update && apt-get install -y \
        libicu-dev \
        libpq-dev \
        libbz2-dev \
        php-pear \
        mc \
        vim \
        wget \
        cron \
        libevent-dev \
        librabbitmq-dev \
        libxml2 \
        libxslt-dev \
    && docker-php-ext-install xsl \
    && docker-php-ext-install iconv \
    && docker-php-ext-install zip \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install intl \
    && docker-php-ext-install pgsql pdo pdo_pgsql \
    && docker-php-ext-install pdo_mysql mysqli \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install opcache \
    && docker-php-ext-enable opcache \
    && apt-get install -y -q --no-install-recommends \
       ssmtp

# Install mcrypt
RUN apt-get install -y libmcrypt-dev
RUN docker-php-ext-install mcrypt

# Install GD
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
    && docker-php-ext-configure gd \
          --enable-gd-native-ttf \
          --with-freetype-dir=/usr/include/freetype2 \
          --with-png-dir=/usr/include \
          --with-jpeg-dir=/usr/include \
    && docker-php-ext-install gd \
    && docker-php-ext-enable gd

# Install Imagick
RUN apt-get install -y \
       libmagickwand-dev \
    && pecl install imagick \
    && docker-php-ext-enable imagick

# Install EXIF
RUN docker-php-ext-install exif \
    && docker-php-ext-enable exif

# Finallly
RUN  apt-get clean \
 && rm -rf /var/lib/apt/lists/*