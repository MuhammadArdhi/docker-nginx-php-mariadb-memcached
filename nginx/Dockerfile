FROM nginx 

# Delete and add new nginx.conf file
RUN rm /etc/nginx/nginx.conf
ADD ./nginx.conf /etc/nginx/nginx.conf

ADD ./default.conf /etc/nginx/conf.d/

RUN echo "daemon off;" >> /etc/nginx/nginx.conf

CMD service nginx start

