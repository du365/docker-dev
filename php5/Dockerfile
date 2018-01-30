FROM php:5-fpm-alpine
RUN apk add --no-cache \
        freetype-dev \
        libjpeg-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        icu-dev \
        msmtp \
    && NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) \
    && docker-php-ext-install -j${NPROC} iconv mcrypt pdo pdo_mysql mysqli\
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j${NPROC} gd intl zip mbstring

RUN ln -sf /usr/bin/msmtp /usr/sbin/sendmail
RUN ln -sf /dev/stdout ~/msmtp.log
