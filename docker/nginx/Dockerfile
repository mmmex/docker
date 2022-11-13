FROM alpine

RUN apk update \
    && apk upgrade \
    && apk add nginx \
    && ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log \
    && echo '<h1>Hello from docker</h1>' > /var/www/index.html

COPY ./default.conf /etc/nginx/http.d/default.conf

EXPOSE 8080

STOPSIGNAL SIGQUIT

CMD ["nginx", "-g", "daemon off;"]

