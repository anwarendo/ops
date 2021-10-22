FROM ubuntu:21.04

RUN apt-get update -y && \
    apt-get install tzdata -y && \
    apt-get install apache2 -y && \
    apt-get install nano -y

COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf

ENTRYPOINT [ "apachectl", "-D", "FOREGROUND"]