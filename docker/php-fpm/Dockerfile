FROM alpine

RUN apk update \
    && apk upgrade \
    && apk add php php-fpm php-opcache php-gd php-mysqli php-zlib php-curl \
    && sed -i 's/^listen = .*/listen = 0.0.0.0:9000/' /etc/php8/php-fpm.d/www.conf && \
    ln -sf /dev/stderr /var/log/php8/error.log

STOPSIGNAL SIGQUIT

EXPOSE 9000

CMD ["/usr/sbin/php-fpm8","-F"]