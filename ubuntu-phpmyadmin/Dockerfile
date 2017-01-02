FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y sudo vim openssh-server git apache2 mysql-client php libapache2-mod-php php-mcrypt php-mysql php-mbstring php-gettext php-curl phpmyadmin

RUN adduser ubuntu --disabled-password
RUN chown -R ubuntu:ubuntu /home/ubuntu
