FROM php:5.6-fpm

RUN apt-get update \
    && DEBIAN_FRONTEND=non-interactive  apt-get install -yq --no-install-recommends \
        curl \
        geoip-database \
        graphviz \
        php5-apcu \
        php5-curl \
        php5-gd \
        php5-geoip \
        php5-intl \
        php5-json \
        php5-ldap \
        php5-mcrypt \
        php5-mysql \
        php5-xsl \
    && docker-php-ext-install mbstring \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/* \
    echo "memory_limit=-1" > $PHP_INI_DIR/conf.d/memory_limit.ini \
    echo "date.timezone=${PHP_TIMEZONE:-UTC}" > $PHP_INI_DIR/conf.d/date_timezone.ini

# PHP Extensions
# RUN docker-php-ext-install curl geoip intl json ldap mbstring mcrypt mysql xsl\
#    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#    && docker-php-ext-install gd

COPY . /var/symfony

VOLUME /var/symfony

WORKDIR /var/symfony

