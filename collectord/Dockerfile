FROM debian:jessie

MAINTAINER André Wiedemann <andre@freshest.me>

ENV COLLECTORD_VERSION 1.7
ENV DEBIAN_FRONTEND noninteractive
ENV TERM xterm

# Install dependencies
RUN apt-get update && apt-get upgrade -y --force-yes && apt-get install -y --force-yes --no-install-recommends apt-utils
RUN apt-get -y --force-yes install \
apt-transport-https \
build-essential \
vim \
wget \
perl

# setup
RUN echo Europe/Berlin > /etc/timezone && dpkg-reconfigure tzdata

# install collectord
RUN wget https://svn.fhem.de/trac/export/HEAD/trunk/fhem/contrib/PRESENCE/deb/collectord-${COLLECTORD_VERSION}.deb && dpkg -i collectord-${COLLECTORD_VERSION}.deb
RUN service collectord stop
RUN rm /etc/init.d/collectord

WORKDIR "/opt/collectord"

COPY config/collectord.conf ./

EXPOSE 5222

ENTRYPOINT ["perl", "/usr/sbin/collectord", "-c", "/opt/collectord/collectord.conf", "-vv"]
