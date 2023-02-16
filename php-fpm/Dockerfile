ARG LARADOCK_PHP_VERSION
FROM php:${LARADOCK_PHP_VERSION}-fpm

#切换清华镜像
RUN sed -i 's/deb.debian.org/mirrors.tuna.tsinghua.edu.cn/' /etc/apt/sources.list && \
    sed -i 's/security.debian.org/mirrors.tuna.tsinghua.edu.cn/' /etc/apt/sources.list && \
    sed -i 's/security-cdn.debian.org/mirrors.tuna.tsinghua.edu.cn/' /etc/apt/sources.list

# Libs
RUN apt-get update \
    && apt-get install -y zlib1g-dev libicu-dev g++ libpq-dev libpng-dev libssl-dev gettext libxml2-dev libzip-dev

#Gettext 用于系统的国际化(I18N)和本地化(L10N),可以在编译程序的时候使用本国语言支持
RUN docker-php-ext-install gettext

#mysqli
RUN docker-php-ext-install mysqli

# Bcmath 高精度运算的函数库
RUN docker-php-ext-install bcmath

RUN docker-php-ext-install gd pcntl pdo_mysql shmop soap sockets sysvsem xmlrpc zip

RUN set -eux; \
    pecl install swoole-4.5.11; \
    docker-php-ext-enable swoole;

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

RUN set -xe; php -v | head -n 1 | grep -q "PHP ${LARADOCK_PHP_VERSION}."

ARG LOCALE=POSIX
ENV LC_ALL ${LOCALE}

WORKDIR /var/www

#CMD ["php-fpm"]

EXPOSE 9000