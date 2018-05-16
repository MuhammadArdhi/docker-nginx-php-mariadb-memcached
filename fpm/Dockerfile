FROM ubuntu:16.04

RUN apt-get update && apt-get install -y software-properties-common language-pack-en-base \
  && LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
  && apt-get update \
  && apt-get install -y php5.6 php5.6-fpm php5.6-mysql mcrypt php5.6-gd curl \
     php5.6-curl php5.6-mbstring php5.6-dev php5.6-xml php5.6-memcached sendmail supervisor \
  && mkdir /run/php \
  && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN apt-get update && apt-get install -y memcached procps netcat

RUN echo "extension='/usr/lib/php/20131226/memcached.so'" >> /etc/php/5.6/fpm/php.ini

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN sed -i -e 's/listen = \/run\/php\/php5.6-fpm.sock/listen = 0.0.0.0:9000/g' /etc/php/5.6/fpm/pool.d/www.conf \
  && sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php/5.6/fpm/php-fpm.conf

WORKDIR /var/www

EXPOSE 9000
EXPOSE 11211

CMD service memcached start
CMD ["/usr/bin/supervisord"]
