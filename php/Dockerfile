FROM khanhicetea/php7-fpm-docker:latest

RUN add-apt-repository ppa:ondrej/php && apt-get update && apt-get install -y --force-yes php-redis && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ARG GITHUB_TOKEN
ENV GITHUB_TOKEN ${GITHUB_TOKEN}

ADD ./auth.json /root/.composer/auth.json

RUN composer self-update
RUN sed -i -e "s/SECRET_TOKEN/$GITHUB_TOKEN/" /root/.composer/auth.json
RUN composer global require "hirak/prestissimo:^0.3"
RUN rm -rf /root/.composer/cache
RUN mkdir /root/.composer/cache

RUN curl -L -O http://deployer.org/deployer.phar && mv deployer.phar /usr/local/bin/dep && chmod +x /usr/local/bin/dep

VOLUME /www
VOLUME /root/.composer/cache
