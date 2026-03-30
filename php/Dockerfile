FROM php:8.4-fpm

# GD 설치에 필요한 패키지 설치
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg-dev \
    libpng-dev \
    libwebp-dev \
    libxpm-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp --with-xpm \
    && docker-php-ext-install mysqli pdo pdo_mysql gd

# Composer 설치
ENV COMPOSER_ALLOW_SUPERUSER=1
COPY --from=composer:2.8.8 /usr/bin/composer /usr/bin/composer

# PS C:\Users\user\gnu50> cd app
# PS C:\Users\user\gnu50\app> git clone https://github.com/pdy1207/gnuboard5.git public
# 그누보드 5 페이지 들어가서 mkdir data -> chmod 707 data 입력 후 새로고침 
# 이후 db 이 이름이 host이름