# https://m.habr.com/post/337306/

FROM ubuntu:latest

RUN apt-get update && apt-get install nginx

ADD ./nginx.conf /etc/nginx/

EXPOSE 80

CMD [nginx]