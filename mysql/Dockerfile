FROM mysql:latest

RUN chown -R mysql:root /var/lib/mysql/

ARG MYSQL_DATABASE
ARG MYSQL_USER
ARG MYSQL_PASSWORD
ARG MYSQL_ROOT_PASSWORD

ENV MYSQL_DATABASE=$MYSQL_DATABASE
ENV MYSQL_USER=$MYSQL_USER
ENV MYSQL_PASSWORD=$MYSQL_PASSWORD
ENV MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD

ADD data.sql /etc/mysql/data.sql

RUN sed -i 's/MYSQL_DATABASE/'$MYSQL_DATABASE'/g' /etc/mysql/data.sql
RUN cp /etc/mysql/data.sql /docker-entrypoint-initdb.d
RUN mysql -u root -p ${MYSQL_ROOT_PASSWORD} -e "ALTER USER '${MYSQL_USER}' IDENTIFIED WITH mysql_native_password BY '${MYSQL_PASSWORD}'"; \
    mysql -u root -p ${MYSQL_ROOT_PASSWORD} -e "flush privileges";

EXPOSE 3306