FROM centos:7
MAINTAINER Jakov Sosic "<jsosic@gmail.com>"
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
 && yum -y update \
 && yum -y install @development git rpm-build yum-utils rpmdevtools sudo openssl which vim \
 && yum clean all
RUN sed -i 's/requiretty/!requiretty/' /etc/sudoers && echo 'jsosic ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers.d/wheel_jsosic && chmod 0400 /etc/sudoers.d/wheel_jsosic \
 && groupadd -g 1505 jsosic && useradd -u 1505 -g 1505 -d /home/jsosic -p `openssl passwd -1 "jsosic"` jsosic \
 && sudo -ujsosic rpmdev-setuptree \
 && sudo -ujsosic echo '%_topdir %(echo $HOME)/jsosic' > ~/.rpmmacros
ENV HOME=/home/jsosic
USER jsosic
WORKDIR /home/jsosic/rpms
