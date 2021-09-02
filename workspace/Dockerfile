FROM   ubuntu:20.04 
RUN apt-get update
RUN apt-get upgrade -y
RUN DEBIAN_FRONTEND=noninteractive apt-get -yq install php
RUN apt-get install php-cli php-zip php-json php-mbstring php-xml -y
RUN apt-get install wget unzip -y
RUN wget -O /home/composer-setup.php  https://getcomposer.org/installer

ENV COMPOSER_INSTALL_FILE /home/composer-setup.php

RUN php $COMPOSER_INSTALL_FILE --install-dir=/usr/local/bin --filename=composer
RUN composer global require cviebrock/eloquent-sluggable
#RUN composer create-project laravel/laravel --prefer-dist /var/www/html/laravel
#RUN chmod -cR 777 /var/www/html/laravel/
RUN apt-get install apache2 -y
RUN echo service apache2 start > /etc/start.sh

RUN a2enmod rewrite


ENV MYPATH /var/www/
WORKDIR $MYPATH

CMD sh /etc/start.sh && tail -f /var/log/apache2/error.log
