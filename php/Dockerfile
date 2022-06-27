FROM php:8.0-apache-bullseye

RUN apt-get update \
 && apt-get install -y zlib1g-dev libzip-dev unzip\
 && docker-php-ext-install zip

RUN curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer \
  && chmod +x /usr/local/bin/composer

# php artisan migrateをするのに必要
RUN docker-php-ext-install pdo_mysql

# これがないと/以外のパスに移動できない
RUN cd /etc/apache2/mods-enabled \
    && ln -s ../mods-available/rewrite.load

# npmを使うための設定
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN rm -rf node_modules
RUN apt-get install -y nodejs
RUN npm install npm -g n --save-dev

WORKDIR /var/www/html

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

ENV TZ=Asia/Tokyo

