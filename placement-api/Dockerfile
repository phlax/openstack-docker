# phlax/placement
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    python3-pymysql placement-api

CMD ["/usr/bin/uwsgi_python37", "--http-socket", "[::]:8778", "--ini", "/etc/placement/placement-api-uwsgi.ini", "--pyargv", "--config-file=/etc/placement/placement.conf"]
