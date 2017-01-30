FROM alpine:3.5
MAINTAINER Wodby <admin@wodby.com>

RUN apk add --no-cache bash
RUN apk add --no-cache tzdata
RUN apk add --no-cache pwgen
RUN apk add --no-cache mariadb=10.1.20-r0
RUN apk add --no-cache mariadb-client=10.1.20-r0

RUN mkdir -p /var/run/mysqld
RUN chown 100:101 /var/run/mysqld

RUN mkdir /docker-entrypoint-initdb.d
COPY my.cnf /etc/mysql/my.cnf
COPY docker-entrypoint.sh /usr/local/bin/

WORKDIR /var/lib/mysql
VOLUME /var/lib/mysql

EXPOSE 3306

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld"]
