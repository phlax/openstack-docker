# phlax/debian:buster-slim
#
# VERSION       0.0.1

ARG BUILD_FROM=debian:buster-slim

# Root stage
FROM $BUILD_FROM

MAINTAINER Ryan Northey <ryan@synca.io>

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update \
    && apt install \
         -y -qq \
	 --no-install-recommends \
         apt-transport-https \
         ca-certificates \
	 wait-for-it \
         wget \
         gnupg2 \
         software-properties-common \
         locales
ONBUILD RUN apt update && apt dist-upgrade -y -qq
