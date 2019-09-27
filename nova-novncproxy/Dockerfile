# phlax/nova-novncproxy
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    nova-common
RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    nova-novncproxy

CMD ["wait-for-it", "nova-api:8774", "--", "/usr/bin/python3", "/usr/bin/nova-novncproxy", "--config-file=/etc/nova/nova.conf"]
