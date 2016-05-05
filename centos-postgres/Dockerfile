#Base Image, built for extension
FROM centos:centos7
MAINTAINER Mahlatse Makalancheche <matt.mahlatse@gmail.com>

#Repo Updates
RUN yum -y update; yum clean all
RUN yum -y install sudo epel-release; yum clean all

#Setting Variables
ENV PG_MAJOR_VERSION 9.5
ENV PG_MAJOR 95
ENV PG_MINOR_VERSION 2
RUN rpm -Uvh http://yum.postgresql.org/$PG_MAJOR_VERSION/redhat/rhel-7-x86_64/pgdg-centos$PG_MAJOR-$PG_MAJOR_VERSION-$PG_MINOR_VERSION.noarch.rpm
RUN yum -y install postgresql$PG_MAJOR-server postgresql$PG_MAJOR supervisor; yum clean all

ADD ./postgresql-setup /usr/bin/postgresql-setup
ADD ./supervisord.conf /etc/supervisord.conf

RUN chmod +x /usr/bin/postgresql-setup

RUN /usr/bin/postgresql-setup initdb

ADD ./postgresql.conf /var/lib/pgsql/data/postgresql.conf

RUN chown -v postgres.postgres /var/lib/pgsql/data/postgresql.conf

RUN echo "host    all             all             0.0.0.0/0               md5" >> /var/lib/pgsql/data/pg_hba.conf

VOLUME ["/var/lib/pgsql"]

CMD ["/bin/bash"]
