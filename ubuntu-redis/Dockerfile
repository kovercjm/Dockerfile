# -------------------------------------------------
# Base image for Ubuntu with redis service
#
# Author: Kover CHENG (jueming.cheng@gmail.com)
# Updated: 12 Sept 2023
# -------------------------------------------------

ARG UBUNTU_VERSION=latest
FROM ubuntu:${UBUNTU_VERSION}

ENV DEBIAN_FRONTEND="noninteractive"

RUN apt update && \
    apt install --no-install-recommends -y \
      software-properties-common \
      gpg-agent \
      ca-certificates

RUN add-apt-repository ppa:redislabs/redis

RUN apt update && \
    apt install --no-install-recommends -y redis && \
    rm -rf /var/lib/apt/lists/* && \
    redis-server /etc/redis/redis.conf
