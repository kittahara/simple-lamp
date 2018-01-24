#
# app
# apache + php
#
FROM php:7.2-apache
MAINTAINER kittahara

COPY /config/*.conf /etc/apache2/sites-enabled/

# :TODO if necessary
RUN mkdir /etc/apache2/ssl
COPY /config/ssl/* /etc/apache2/ssl/
RUN mv /etc/apache2/ssl/openssl.cnf /etc/ssl/openssl.cnf
RUN chmod 600 /etc/apache2/ssl/*

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
RUN apt-get install  -y libpq-dev libxml2-dev libpng-dev
RUN docker-php-ext-install pdo pdo_mysql mbstring tokenizer xml gd pcntl zip
# mod_rewrite,openssl enable
RUN a2enmod rewrite ssl

# :TODO if necessary
RUN apt-get install  -y vim
# 以下はcomposer updateに必要なため
RUN apt-get install  -y git unzip telnet net-tools
