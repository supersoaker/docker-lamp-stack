FROM php:7.1-apache	
# or php:7.0-apache, php:5.6-apache @see https://github.com/docker-library/php

# @see https://gist.github.com/tristanlins/4c1da2508f0326a042aa
# install imagick
RUN apt-get update \
    && apt-get install -y \
        libmagickwand-dev \
    && rm -rf /var/lib/apt/lists/* \
    && pecl install imagick-beta \
    && echo "extension=imagick.so" > /usr/local/etc/php/conf.d/ext-imagick.ini \
    && apt-get remove -y \
        libmagickwand-dev \
    && apt-get install -y \
        libmagickwand-6.q16-2 \
    && apt-get autoremove -y

RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/ssl-cert-snakeoil.key -out /etc/ssl/certs/ssl-cert-snakeoil.pem -subj "/C=AT/ST=Vienna/L=Vienna/O=Security/OU=Development/CN=example.com"
RUN a2enmod ssl
