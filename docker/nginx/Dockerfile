FROM nginx:stable-alpine

RUN apk --update --no-cache add curl && \
    mkdir -p /var/www && \
    curl -SL https://download.pydio.com/pub/core/archives/pydio-core-8.0.2.tar.gz | tar xz --strip-components=1 -C /var/www

COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf
COPY ./docker/nginx/nginx.conf /etc/nginx/nginx.conf

VOLUME /var/www

WORKDIR /var/www

