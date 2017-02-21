FROM centos:7
MAINTAINER "xuan" <admin@exuan.org>
ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*; \
yum -y update; \
rpm –import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org; \
yum install -y http://www.elrepo.org/elrepo-release-7.0-9.el7.elrepo.noarch.rpm; \
yum –enablerepo=elrepo-kernel install -y kernel-ml; \
yum install -y epel-release && yum update; \
yum install -y wget gcc autoconf libxml2 libxml2-devel openssl openssl-devel libcurl libcurl-devel libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel libmcrypt libmcrypt-devel bzip2; \
yum clean all

EXPOSE 6379 2000 3306 8000 80

VOLUME ["/sys/fs/cgroup", "/data/website", "/data/workspace", "/data/gospace"]
CMD ["/usr/sbin/init"]