FROM debian:jessie

MAINTAINER André Wiedemann <andre@freshest.me>

ENV DEBIAN_FRONTEND noninteractive
ENV TERM xterm

# Install dependencies
RUN apt-get update && apt-get upgrade -y --force-yes && apt-get install -y --force-yes --no-install-recommends apt-utils
RUN apt-get -y --force-yes install \
apt-transport-https \
build-essential \
perl \
vim \
wget

# Install perl packages
RUN apt-get -y --force-yes install \
libio-socket-ip-perl \
libio-socket-multicast-perl \
libjson-perl \
libjson-xs-perl \
libsoap-lite-perl \
libsocket-perl \
libsocket6-perl \
libwww-perl \
libxml-simple-perl \
libxml-parser-lite-perl

# setup
RUN echo Europe/Berlin > /etc/timezone && dpkg-reconfigure tzdata

WORKDIR "/opt/fhem"

EXPOSE 4711

CMD ["perl", "./FHEM/00_SONOS.pm", "4711", "1", "1"]
