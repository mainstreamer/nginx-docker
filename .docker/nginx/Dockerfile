FROM nginx:stable-alpine3.17

RUN apk add --update \
    acl \
    shadow
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*
ADD .docker/nginx/nginx.conf /etc/nginx/
RUN mkdir -p /etc/nginx/certs
ADD .docker/nginx/certs/* /etc/nginx/certs/
#ADD .docker/nginx/certs/* /etc/ssl/*
RUN rm /etc/nginx/conf.d/default.conf
#RUN mkdir -p /etc/nginx/templates && echo -e 'upstream php-upstream { server $PHP_UPSTREAM:9000; }' > /etc/nginx/templates/upstream.conf.template
ADD content /var/www/html
RUN getent group www-data || addgroup www-data
RUN adduser -D -g '' -G www-data www-data
RUN usermod -u 1000 www-data
CMD ["nginx"]
EXPOSE 80
EXPOSE 443
ADD .docker/nginx/templates/* /etc/nginx/templates/