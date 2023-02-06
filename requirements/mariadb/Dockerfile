FROM debian:buster


#open port for mariadb (mandatory)
EXPOSE 3306

RUN apt-get upgrade -y \
&& apt-get update -y 

#install procps for
RUN apt-get install -y procps

RUN apt-get install -y mariadb-server

#rm base configuration of mariadb then copy the new one made by myself

RUN rm /etc/mysql/mariadb.conf.d/50-server.cnf

COPY	conf/50-server.cnf /etc/mysql/mariadb.conf.d

#copy my script for db 
COPY tools/init.sh ./
COPY tools/init_db.sql ./

#creat files for database

RUN mkdir -p /var/run/mysqld/


#give right acces for files

RUN		chown -R mysql:mysql /var/lib/mysql && \
		chmod 777 /var/lib/* && \
		chmod +x init.sh
#exec mu script for init

CMD		"./init.sh"

