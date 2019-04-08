FROM ubuntu:18.04
MAINTAINER "Jakov Sosic" <jsosic@gmail.com>
ENV container docker

ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive
RUN sed -i 's/# deb/deb/g' /etc/apt/sources.list

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN apt-get update \
    && apt-get install -y systemd \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do \
        [[ $i == systemd-tmpfiles-setup.service ]] || rm -f $i; \
     done); \
    rm -f /lib/systemd/system/multi-user.target.wants/*; \
    rm -f /etc/systemd/system/*.wants/*; \
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \ 
    rm -f /lib/systemd/system/basic.target.wants/*; \
    rm -f /lib/systemd/system/anaconda.target.wants/*; \
    rm -f /lib/systemd/system/plymouth*; \
    rm -f /lib/systemd/system/systemd-update-utmp*

WORKDIR /root
VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
