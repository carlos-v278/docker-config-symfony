FROM php:8.1-apache


RUN curl -sSLf \
    -o /usr/local/bin/install-php-extensions \
    https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions pdo_pgsql intl  

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip pip

RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
    mv composer.phar /usr/local/bin/composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

RUN curl -sL https://deb.nodesource.com/setup_18.x | bash 
RUN apt install nodejs -yq 

ENV COMPOSER_ALLOW_SUPERUSER=1

RUN cd /var/www


RUN git config --global user.email "carlosvieira278@gmail.com" && \
     git config --global user.name "carlos"

WORKDIR /var/www
EXPOSE 80

