FROM mysql:latest

RUN chown -R mysql:root /var/lib/mysql/

ENV MYSQL_DATABASE=dd
ENV MYSQL_USER=mydbuser
ENV MYSQL_PASSWORD=qwerty
ENV MYSQL_ROOT_PASSWORD=qwe123rty

ADD data.sql /etc/mysql/data.sql

RUN sed -i 's/MYSQL_DATABASE/'$MYSQL_DATABASE'/g' /etc/mysql/data.sql
RUN cp /etc/mysql/data.sql /docker-entrypoint-initdb.d
RUN mysql -u root -p ${MYSQL_ROOT_PASSWORD} -e "ALTER USER '${MYSQL_USER}' IDENTIFIED WITH mysql_native_password BY '${MYSQL_PASSWORD}';" \
    mysql -u root -p ${MYSQL_ROOT_PASSWORD} -e "flush privileges;"

EXPOSE 3306