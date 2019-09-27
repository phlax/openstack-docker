# phlax/openstack
#
# VERSION       0.0.1

ARG BUILD_FROM=debian:buster-slim

# Root stage
FROM $BUILD_FROM

MAINTAINER Ryan Northey <ryan@synca.io>

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y -qq \
    apt-transport-https \
    ca-certificates \
    wget \
    gnupg2 \
    software-properties-common
RUN wget -qO - http://buster-stein.debian.net/debian/dists/pubkey.gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] http://buster-stein.debian.net/debian/ \
   buster-stein-backports main"
RUN add-apt-repository \
   "deb [arch=amd64] http://buster-stein.debian.net/debian/ \
   buster-stein-backports-nochange main"

RUN apt update \
    && apt install \
        -y -qq --no-install-recommends \
	python3-openstackclient -t buster-stein-backports
