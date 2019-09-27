# phlax/horizon
#
# VERSION       0.0.1

ARG BUILD_FROM=httpd:2.4

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
        --no-install-recommends -y -qq \
	-t buster-stein-backports \
	openstack-dashboard-apache

RUN /usr/share/openstack-dashboard/manage.py compress
RUN /usr/share/openstack-dashboard/manage.py collectstatic --noinput

RUN chown www-data:www-data -R /var/lib/openstack-dashboard

COPY bin/apache-run /usr/local/bin/apache-run

STOPSIGNAL SIGWINCH

CMD ["apache-run"]
