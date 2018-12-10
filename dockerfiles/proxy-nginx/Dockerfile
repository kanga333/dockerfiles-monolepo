FROM nginx:1.15.7-alpine-perl

RUN mkdir /public && chown -R nginx:nginx /public

ENV BACKEND_ADDR=127.0.0.1
ENV BACKEND_PORT=8080

RUN rm -f /etc/nginx/conf.d/default.conf
COPY ./files/nginx.conf   /etc/nginx/
COPY ./files/service.conf /etc/nginx/conf.d

EXPOSE 80

ENTRYPOINT /usr/sbin/nginx -g 'daemon off;'

ARG GIT_REVISION=unknown
ARG GIT_ORIGIN=unknown
ARG IMAGE_NAME=unknown
LABEL git-revision=$GIT_REVISION \
      git-origin=$GIT_ORIGIN \
      image-name=$IMAGE_NAME
