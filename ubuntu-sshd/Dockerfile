# -------------------------------------------------
# Base image of Ubuntu with SSHD service
#
# Author: Kover CHENG (jueming.cheng@gmail.com)
# Updated: 30 Nov 2020
# -------------------------------------------------

ARG UBUNTU_VERSION=latest
FROM ubuntu:${UBUNTU_VERSION}

# Install openssh-server in the cleanest way
RUN DEBIAN_FRONTEND="noninteractive" apt update && \
  apt install -y --no-install-recommends openssh-server sudo && \
  rm -rf /var/lib/apt/lists/*

# Setup SSHD environment & User account info
# Please change the PASSWORD before you use
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 userName && \
  echo 'userName:Passw0rd' | chpasswd && \
  mkdir /var/run/sshd && \
  sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config  && \
  sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

# Expose SSH Port
EXPOSE 22

# Start SSHD Service
CMD ["/usr/sbin/sshd", "-D"]
