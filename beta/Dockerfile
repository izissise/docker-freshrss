FROM php:5.6-apache
MAINTAINER Guillaume Fillon <guillaume@posteo.de>

RUN apt-get update && \
    apt-get install -y libcurl4-openssl-dev libjpeg62-turbo-dev \
    libmcrypt-dev libpng12-dev libicu-dev libgmp-dev libsqlite3-dev && \
    ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/include/gmp.h && \
    docker-php-ext-install curl mbstring gd intl mysql json zip gmp \
        pdo pdo_mysql pdo_sqlite

WORKDIR /var/www/html

COPY freshrss /var/www/html
COPY freshrss/data /data
COPY run.sh /run.sh

RUN chown -R :www-data /var/www/html
RUN chmod -R g+w /var/www/html/data
RUN chmod +x /run.sh

VOLUME ["/var/www/html/data"]

CMD ["/run.sh"]
