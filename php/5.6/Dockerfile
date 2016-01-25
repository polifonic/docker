FROM php:5.6-fpm

RUN apt-get update \
    && DEBIAN_FRONTEND=non-interactive  apt-get install -yq --no-install-recommends \
    	curl \
    	php-curl \
		php5-gd \
		php5-geoip \
		php5-intl \
		php5-json \
		php5-ldap \
		php5-mcrypt \
		php5-mysql \
		php5-xsl \
		graphviz
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/* \

COPY php.ini /usr/local/php/$PHP_VERSION/etc/conf.d/local.ini

RUN composer self-update

RUN mkdir ~/.ssh \
	&& ssh-keyscan -H bitbucket.org >> /root/.ssh/known_hosts \
	&& ssh-keyscan -H github.com >> /root/.ssh/known_hosts \
	&& ssh-keyscan -H gitlab.united-asian.com >> /root/.ssh/known_hosts

