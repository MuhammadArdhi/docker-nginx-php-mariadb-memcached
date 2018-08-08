# docker-nginx-php-mariadb-memcached
Docker running Nginx, PHP-FPM, MariaDB &amp; Memcached

## Prerequisite
Install Docker: https://docs.docker.com/install/

## Usage
1. Create directory var/lib/mariadb 
2. Create directory var/log/nginx and create a file error.logs
3. Clone your project from Git into directory www/ or you can just copy paste your project to here.
4. Copy file memcached.php into `www/application/config` if you using CodeIgniter framework.
5. Define your environment variables on .env file
6. Running command docker-compose up -d (or without argument -d to see the process) to start containers
7. Import your database into mariadb server using this command 
```
docker exec -i CONTAINER_ID /bin/bash -c "export TERM=xterm && mysql -uroot -prootpasswd database" < import.sql
```

## Note
- In this case I used version 3 of docker-compose and Docker engine version 18.03.0.
- The nginx config in directory nginx is very simple, please customize with your requirements.
