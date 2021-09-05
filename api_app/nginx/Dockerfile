FROM ubuntu:16.04

MAINTAINER Chris Fidao

RUN apt-get update \
    && apt install -y software-properties-common \
    && apt-get install -y nginx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && echo "daemon off;" >> /etc/nginx/nginx.conf

RUN add-apt-repository ppa:certbot/certbot \
        && apt update \
        && apt-get install -y certbot

ADD Default /etc/nginx/sites-available/default

EXPOSE 80
CMD ["nginx"]
