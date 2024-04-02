FROM docker.io/nginx:stable-alpine-slim

RUN rm /etc/nginx/conf.d/*

COPY files/nginx.conf /etc/nginx/nginx.conf
COPY files/index.html /usr/share/nginx/html/index.html