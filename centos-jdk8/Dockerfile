#Base Image, built for extension
FROM centos:centos7
MAINTAINER Mahlatse Makalancheche <matt.mahlatse@gmail.com>

#Repo Updates
RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all

#Set Variables
ENV JAVA_VERSION 8u92
ENV BUILD_VERSION b14
ENV JDK /tmp/jdk.rpm

#Installation
RUN yum -y install wget && \
    wget --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSION-$BUILD_VERSION/jdk-$JAVA_VERSION-linux-x64.rpm" -O $JDK && \
    yum -y install $JDK && \
    rm -f $JDK && \
    yum clean all

ENV JAVA_HOME /usr/java/latest

CMD ["/bin/bash"]

