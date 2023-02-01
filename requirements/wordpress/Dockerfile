FROM debian:buster

EXPOSE 9000

RUN apt-get upgrade -y \
&& apt-get update -y \
&& apt-get -y install wget \
&& mkdir -p /var/www/html \
&& mkdir -p /run/php/php7.3-fpm \
&& cd /var/www \
&& wget http://fr.wordpress.org/latest-fr_FR.tar.gz \
&& tar -xzvf latest-fr_FR.tar.gz \
&& mv wordpress wp 



RUN apt-get install -y postfix

RUN	apt-get install -y curl
RUN apt-get -y install php7.3 php7.3-fpm php7.3-mysql php-common php7.3-json php7.3-readline 




COPY conf/www.conf /etc/php/7.3/fpm/pool.d/
COPY	conf/wp-config.php ./
COPY tools/init.sh ./


RUN	curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar 
RUN	chmod +x wp-cli.phar init.sh
RUN	mv wp-cli.phar /usr/local/bin/wp

RUN chown -R www-data. /var/www/html


CMD "./init.sh"
