FROM ubuntu:16.04

RUN apt-get update && apt-get install -y software-properties-common language-pack-en-base \
  && LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
  && LC_ALL=en_US.UTR-8 add-apt-repository -y ppa:nginx/stable \
  && apt-get update \
  && apt-get install -y php5.6 php5.6-fpm php5.6-mysql mcrypt php5.6-gd curl \
     php5.6-curl php5.6-mbstring php5.6-dev php5.6-xml php5.6-memcached sendmail supervisor \
     nginx-full vim \
  && mkdir /run/php \
  && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# nginx
ADD ./nginx.conf /etc/nginx/nginx.conf
ADD ./default.conf /etc/nginx/conf.d/
# php-fpm
RUN rm /etc/php/5.6/fpm/php.ini
ADD ./php.ini /etc/php/5.6/fpm/
ADD ./php-fpm.conf /etc/php/5.6/fpm/php-fpm.conf
ADD ./uploads.ini /etc/php/5.6/fpm/conf.d/uploads.ini
ADD ./www.conf /etc/php/5.6/fpm/pool.d/www.conf

RUN chown -R www-data:www-data /var/www
RUN chown -R 755 /var/www

COPY ./supervisord.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 80

CMD ["/usr/bin/supervisord"]
