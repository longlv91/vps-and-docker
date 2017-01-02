FROM centos:centos7

RUN yum -y update
RUN yum install -y vim openssh-server git
RUN yum -y provides ifconfig
RUN yum -y install net-tools

RUN adduser hathanhtam -p hathanhtam
RUN chown -R hathanhtam:hathanhtam /home/hathanhtam

