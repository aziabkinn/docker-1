FROM ruby

RUN apt-get update -y && apt-get upgrade -y \
    && gem install rails \
    && apt-get install nodejs -y

ONBUILD COPY app/ /opt/app

ONBUILD RUN bundle install \
    && rails db:migrate \
    && rails db:seed

WORKDIR /opt/app/

# скачать с https://github.com/rails/rails
# docker build -t ft-rails:on-build .
# docker build -t rails -f Dockerfile.another .
# docker run -it --rm rails sh