FROM fedora:29
MAINTAINER "Jakov Sosic" <jsosic@gmail.com>
ENV container docker

RUN dnf -y update \
 && dnf -y install which less procps-ng \
 && dnf clean all

RUN dnf -y install systemd && dnf clean all

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
