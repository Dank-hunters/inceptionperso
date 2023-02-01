FROM debian:buster

RUN apt-get upgrade -y \
&& apt-get update -y \
&& apt-get -y install wget \
&& mkdir -p /var/www/html \
&& cd /var/www \
&& wget http://fr.wordpress.org/latest-fr_FR.tar.gz \
&& tar -xzvf latest-fr_FR.tar.gz \
&& mv wordpress www 

RUN apt-get -y install php-cli php-mysql php-curl php-gd php-intl
RUN apt-get -y install php-fpm

COPY conf/wp.conf /etc/php/7.4/fpm/pool.d/
