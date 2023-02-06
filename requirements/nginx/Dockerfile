FROM debian:buster

#run upgrade and update then install nginx
RUN apt-get upgrade -y \
&& apt-get update -y \
&& apt-get install -y nginx


#install openssl to created a self signed certificate for https

RUN apt-get install -y openssl \
&& openssl req -x509 -nodes -days 365 -subj "/C=FR/ST=France/L=Lyon/O=42/OU=42/CN=cguiot" -newkey rsa:4096 -keyout /etc/nginx/cert.key -out /etc/nginx/cert.crt



 #copy the set up for the configuration file for nginx
COPY conf/nginx.conf /etc/nginx/sites-enabled

#expose 443 pour ecouter les requetes HTTPS

EXPOSE 443
	
#daemon off is for running nginx on 1st [plan and get debug console, 

CMD	[ "nginx", "-g", "daemon off;" ]
