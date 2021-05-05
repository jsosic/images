FROM centos:6
MAINTAINER Jakov Sosic "<jsosic@gmail.com>"
RUN sed -i 's/mirrorlist=/#mirrorlist=/g' /etc/yum.repos.d/* \
 && sed -i 's|#baseurl=http://mirror.centos.org/|baseurl=http://vault.centos.org/|g' /etc/yum.repos.d/* \
 && yum -y install https://archives.fedoraproject.org/pub/archive/epel/6/x86_64/epel-release-6-8.noarch.rpm \
 && yum -y update \
 && yum -y install @development git rpm-build yum-utils rpmdevtools sudo openssl which vim \
 && yum -y install epel-rpm-macros \
 && yum clean all
RUN sed -i 's/requiretty/!requiretty/' /etc/sudoers && echo 'jsosic ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers.d/wheel_jsosic && chmod 0400 /etc/sudoers.d/wheel_jsosic \
 && groupadd -g 1505 jsosic && useradd -u 1505 -g 1505 -d /home/jsosic -p `openssl passwd -1 "jsosic"` jsosic \
 && sudo -ujsosic rpmdev-setuptree \
 && sudo -ujsosic echo '%_topdir %(echo $HOME)/jsosic' > ~/.rpmmacros
ENV HOME=/home/jsosic
USER jsosic
WORKDIR /home/jsosic/rpms
