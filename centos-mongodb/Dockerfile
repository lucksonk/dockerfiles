#Base Image, built for extension
FROM centos:centos7
MAINTAINER Mahlatse Makalancheche <matt.mahlatse@gmail.com>

#Repo Updates
RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all

#Installation
RUN yum -y install mongodb-server; yum clean all
RUN mkdir -p /data/db

CMD ["/bin/bash"]

