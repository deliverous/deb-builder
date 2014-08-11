FROM deliverous/jessie
MAINTAINER docker@deliverous.com

ENV DEBIAN_FRONTEND noninteractive
# Get src from unstable
RUN echo "deb-src http://ftp.us.debian.org/debian sid main" >> /etc/apt/sources.list
RUN apt-get update && apt-get dist-upgrade -y && apt-get clean

RUN apt-get update && apt-get install -y dpkg-dev devscripts libmicrohttpd-dev dh-systemd && apt-get build-dep -y systemd && apt-get clean
RUN cd /usr/src/ && apt-get source systemd && apt-get clean

ADD Add-systemd-journal-gatewayd-package.patch /tmp/
RUN cd /usr/src/systemd-208/ && patch -p1 < /tmp/Add-systemd-journal-gatewayd-package.patch
RUN cd /usr/src/systemd-208/ && dpkg-buildpackage -B -us -uc

CMD cd /usr/src/ && tar -c *.deb
