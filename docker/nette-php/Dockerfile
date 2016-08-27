FROM php:7.0.9-fpm

RUN apt-get update && apt-get install -y git libpng12-dev libjpeg-dev libpq-dev mysql-client libxml2-dev libmcrypt-dev libbz2-dev build-essential openssh-server supervisor libtool libyaml-dev wget vim nano \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr\
	&& docker-php-ext-install gd mbstring pdo pdo_mysql pdo_pgsql zip json pcntl opcache bcmath bz2 mcrypt soap\
	&& rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

ADD php.ini /usr/local/etc/php/

RUN pecl install xdebug-2.4.1
RUN echo "xdebug.cli_color=1\nxdebug.remote_autostart=1\nxdebug.remote_connect_back=1\nxdebug.idekey=PHPSTORM\nxdebug.remote_enable=1\nxdebug.remote_log=/tmp/xdebug_remote.log" > /usr/local/etc/php/conf.d/xdebug.ini

ENV TZ=Europe/Prague
RUN echo $TZ > /etc/timezone

WORKDIR /app