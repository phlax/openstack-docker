# phlax/nova-compute
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
    nova-compute

CMD ["/usr/bin/python3", "/usr/bin/nova-compute", "--config-file=/etc/nova/nova.conf", "--config-file=/etc/nova/nova-compute.conf"]
