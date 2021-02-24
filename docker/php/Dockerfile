FROM php:7.4-apache
RUN  a2enmod rewrite
RUN apt-get update && \
  apt-get install -y zlib1g-dev libzip-dev unzip && \
  docker-php-ext-install zip pdo_mysql mysqli &&\
  pecl install xdebug && \
  docker-php-ext-enable xdebug
RUN echo 'PassEnv MYSQLCONNSTR_localdb' > /etc/apache2/conf-enabled/expose-env.conf 
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
