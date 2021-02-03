#
# app
# apache + php
#
FROM php:8.0.1-apache
MAINTAINER kittahara

COPY ./container/app/config/*.conf /etc/apache2/sites-enabled/

# :TODO debug page
COPY ./container/app/config/index.php /var/www/html/index.php
RUN echo "phpinfo();" >> /var/www/html/index.php
RUN mkdir /var/www/html/front /var/www/html/admin
COPY ./container/app/config/index.php /var/www/html/front/index.php
RUN echo "echo 'Front !!!!!';" >> /var/www/html/front/index.php
COPY ./container/app/config/index.php /var/www/html/admin/index.php
RUN echo "echo 'Admin !!!!!';" >> /var/www/html/admin/index.php

RUN apt-get update

# php_ext install & enable
RUN apt-get install -y libicu-dev libonig-dev libzip-dev ssl-cert locales
RUN docker-php-ext-install intl pdo_mysql zip bcmath mbstring tokenizer
# mod_rewrite,openssl enable
RUN a2enmod rewrite ssl

RUN apt-get install  -y sudo vim git unzip telnet net-tools wget gnupg

# composer install
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN composer self-update
RUN composer --version

# node,npm install
RUN curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
RUN apt-get install -y nodejs
RUN node --version
RUN npm --version
