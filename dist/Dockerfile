FROM phoenixmedia/nginx-php:8.2

COPY /docker/conf/php/php.ini /etc/php81/php.ini
COPY --chown=nginx:nginx src/ /var/www/html/

RUN su -s /bin/bash nginx -c "/var/www/html/vendor/bin/ece-tools build:generate" && rm -Rf /var/www/html/var/view_preprocessed && rm -f app/etc/env.php

COPY /docker/conf/nginx/default.conf /etc/nginx/conf.d/default.conf
COPY /docker/conf/nginx/header_params /etc/nginx/header_params
COPY /docker/conf/supervisord/supervisord.conf /etc/supervisord.conf
COPY /docker/conf/supervisord/supervisord-cronjob.conf /etc/supervisord-cronjob.conf
COPY /docker/conf/cron/nginx /etc/crontabs/nginx
COPY /helm/ /var/www/html/helm/

ARG BUILD_NUMBER=0
RUN echo "$(/usr/bin/envsubst < /etc/nginx/header_params)" > /etc/nginx/header_params \
    && sed -i -e "s#id_prefix: \"cache_\"#id_prefix: \"${BUILD_NUMBER}_\"#g" /var/www/html/.magento.env.yaml
