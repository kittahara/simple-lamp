#
# app
# apache + php
#
FROM php:7.2-apache
MAINTAINER kittahara

COPY /config/*.conf /etc/apache2/sites-enabled/

# :TODO debug page
COPY /config/index.php /var/www/html/index.php
RUN echo "phpinfo();" >> /var/www/html/index.php
RUN mkdir /var/www/html/front /var/www/html/admin
COPY /config/index.php /var/www/html/front/index.php
RUN echo "echo 'Front !!!!!';" >> /var/www/html/front/index.php
COPY /config/index.php /var/www/html/admin/index.php
RUN echo "echo 'Admin !!!!!';" >> /var/www/html/admin/index.php

RUN apt-get update

# php_ext install & enable
RUN apt-get install  -y libpq-dev libxml2-dev libpng-dev ssl-cert
RUN docker-php-ext-install pdo pdo_mysql mbstring tokenizer xml gd pcntl zip
# mod_rewrite,openssl enable
RUN a2enmod rewrite ssl

RUN apt-get install  -y sudo vim git unzip telnet net-tools wget gnupg

# composer install
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN composer self-update
RUN composer --version

# node,npm install
RUN curl -sL https://deb.nodesource.com/setup_9.x | bash -
RUN apt-get install -y nodejs
RUN node --version
RUN npm --version
