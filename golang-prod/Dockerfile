# -------------------------------------------------
# Base image for Golang production environment
#
# Author: Kover CHENG (jueming.cheng@gmail.com)
# Updated: 30 Aug 2023
# -------------------------------------------------

ARG UBUNTU_VERSION=latest
FROM ubuntu:${UBUNTU_VERSION}

ENV TZ="Asia/Shanghai" DEBIAN_FRONTEND="noninteractive"

RUN apt update && \
    apt install --no-install-recommends -y \
      tzdata \
      ca-certificates \
      curl && \
    rm -rf /var/lib/apt/lists/*
