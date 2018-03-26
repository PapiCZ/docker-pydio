FROM alpine:3.7

RUN apk --update --no-cache add curl && \
    mkdir -p /var/www && \
    curl -SL https://download.pydio.com/pub/core/archives/pydio-core-8.0.2.tar.gz | tar xz --strip-components=1 -C /var/www && \
    apk --update add php7 php7-fpm php7-mysqli php7-pgsql php7-curl php7-json php7-gd php7-intl php7-mbstring php7-xml php7-dom php7-zip php7-exif php7-apcu php7-session php7-opcache php7-iconv && \
    chown -R nobody:nobody /var/www

COPY ./docker/php-fpm/www.conf /etc/php7/php-fpm.d/www.conf
COPY ./docker/php-fpm/php-overrides.ini /etc/php7/conf.d/99_override.ini

VOLUME /var/www

WORKDIR /var/www

EXPOSE 9000

ENTRYPOINT ["/usr/sbin/php-fpm7", "--nodaemonize"]
