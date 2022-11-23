ARG LARADOCK_PHP_VERSION
#FROM php:${LARADOCK_PHP_VERSION}-fpm
FROM bitnami/php-fpm:${LARADOCK_PHP_VERSION}

RUN set -xe; php -v | head -n 1 | grep -q "PHP ${LARADOCK_PHP_VERSION}."

# Clean up
#RUN apt-get clean && \
#    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
#    rm /var/log/lastlog /var/log/faillog \

ARG LOCALE=POSIX
ENV LC_ALL ${LOCALE}

WORKDIR /var/www

#CMD ["php-fpm"]

EXPOSE 9000