FROM ubuntu:18.04

MAINTAINER Nel Ajoc (ronel.ajoc@gmail.com)


WORKDIR /srv/http/laravel

### Update Apt Repository and Install Dependencies ###
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -qq install -y \
    wget \
    zip \
    nginx \
    mysql-client \
    php7.2 \
    php7.2-bcmath \
    php7.2-cli \
    php7.2-common \
    php7.2-curl \
    php7.2-fpm \
    php7.2-gd \
    php7.2-json \
    php7.2-mbstring \
    php7.2-mysql \
    php7.2-xml \
    php7.2-zip


### INSTALL COMPOSER ###
RUN curl -s https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer

### INSTALL LARAVEL ###
RUN composer create-project --prefer-dist laravel/laravel laravel

### SET PERMISSION ###
RUN chown -R www-data:www-data /srv/http/laravel && \
    chmod -R 755 /var/www/laravel

CMD ["/bin/bash", "-c", "/etc/init.d/php7.2-fpm start && nginx -g 'daemon off;'"]