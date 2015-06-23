FROM alpine:edge
MAINTAINER Thibault NORMAND <me@zenithar.org>

RUN apk add --update musl php-fpm php-pdo php-pdo_mysql \
    php-iconv php-gd php-mcrypt php-bcmath php-calendar \
    php-pear php-gmp php-curl php-json php-zlib \
    php-opcache php-mysql php-mysqli php-openssl \
    && rm -rf /var/cache/apk/*

RUN sed -i '/^listen/c \
listen = 0.0.0.0:9000' /etc/php/php-fpm.conf

RUN mkdir -p /srv/http && echo "<?php phpinfo(); ?>" > /srv/http/index.php

EXPOSE 9000
VOLUME /srv/http
ENTRYPOINT ["php-fpm", "-F"]