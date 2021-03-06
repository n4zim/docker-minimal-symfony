FROM debian:jessie

MAINTAINER Nazim Lachter <nlachter@gmail.com>

# Main dependencies
RUN apt-get update && apt-get install -y --force-yes --no-install-recommends \
    ca-certificates \
    curl \
    wget

# For PHP 7 FPM
RUN echo "deb http://packages.dotdeb.org jessie all" > /etc/apt/sources.list.d/dotdeb.list
RUN wget https://www.dotdeb.org/dotdeb.gpg -P /tmp/ && apt-key add /tmp/dotdeb.gpg

# NodeJS (includes an "apt-get update" at the end)
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -

# PHP dependencies
RUN apt-get install -y --force-yes --no-install-recommends \
    php7.0 php7.0-fpm php7.0-mysql php7.0-curl php7.0-json php7.0-gd php7.0-mcrypt \
    php7.0-msgpack php7.0-memcached php7.0-intl php7.0-sqlite3 php7.0-gmp php7.0-geoip \
    php7.0-mbstring php7.0-xml php7.0-zip php7.0-dom

# Software dependencies
RUN apt-get install -y --force-yes --no-install-recommends \
    git \
    nginx \
    nodejs \
    imagemagick \
    libmagickwand-dev \
    supervisor

# NodeJS dependencies
RUN npm install -g \
    bower \
    less

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Empty www folder
RUN rm -r /var/www/*

# Open Ports
EXPOSE 80
EXPOSE 443

# Clean
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
