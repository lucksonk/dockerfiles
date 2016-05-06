#Base Image, built for extension
FROM centos:centos7
MAINTAINER Mahlatse Makalancheche <matt.mahlatse@gmail.com>

#Repo Updates
RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all

#Installation
RUN \
  cd /tmp && \
  yum install -y --enablerepo=epel \
      gcc make \
      wget && \
  yum clean all

RUN wget http://download.redis.io/redis-stable.tar.gz && \
  tar xvzf redis-stable.tar.gz && \
  cd redis-stable && \
  ls -l && \
  make install && \
  cp -f src/redis-sentinel /usr/local/bin && \
  mkdir -p /etc/redis && \
  cp -f *.conf /etc/redis
RUN rm -rf /tmp/redis-stable*
RUN sed -i 's/^\(bind .*\)$/# \1/' /etc/redis/redis.conf && \
    sed -i 's/^\(daemonize .*\)$/# \1/' /etc/redis/redis.conf && \
    sed -i 's/^\(dir .*\)$/# \1\ndir \/data/' /etc/redis/redis.conf && \
    sed -i 's/^\(logfile .*\)$/# \1/' /etc/redis/redis.conf                                                                                                                           
                                                                                                                           
VOLUME ["/data/redis"]

CMD ["/bin/bash"]

