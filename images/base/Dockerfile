FROM ubuntu:precise

RUN echo 'deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe' > /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y upgrade # 20131221

# Hack for initctl not being available in Ubuntu
RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -s /bin/true /sbin/initctl

ENV DEBIAN_FRONTEND noninteractive
