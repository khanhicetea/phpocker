FROM khanhicetea/php7-fpm-docker:latest

ARG GITHUB_TOKEN
ENV GITHUB_TOKEN ${GITHUB_TOKEN}

ADD ./auth.json /root/.composer/auth.json

RUN composer self-update
RUN sed -i -e "s/SECRET_TOKEN/$GITHUB_TOKEN/" /root/.composer/auth.json
RUN composer global require "hirak/prestissimo:^0.3"
RUN rm -rf /root/.composer/cache
RUN mkdir /root/.composer/cache

VOLUME /www
VOLUME /root/.composer/cache
