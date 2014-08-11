FROM deliverous/jessie
MAINTAINER docker@deliverous.com

ENV DEBIAN_FRONTEND noninteractive
RUN echo "deb-src http://ftp.us.debian.org/debian jessie main" >> /etc/apt/sources.list
RUN apt-get update && apt-get dist-upgrade -y && apt-get clean

RUN apt-get update && apt-get install -y dpkg-dev && apt-get clean
RUN cd /usr/src/ && apt-get source systemd && apt-get clean
RUN apt-get build-dep -y systemd && apt-get install -y libmicrohttpd-dev dh-systemd && apt-get clean

CMD cd /usr/src/systemd-208/ 
