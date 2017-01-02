FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive

RUN sed -i 's/http:\/\/archive\.ubuntu.com\/ubuntu\//http:\/\/mirror-fpt-telecom\.fpt\.net\/ubuntu\//g' etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y vim openssh-server git

RUN adduser hathanhtam --disabled-password
RUN chown -R hathanhtam:hathanhtam /home/hathanhtam

