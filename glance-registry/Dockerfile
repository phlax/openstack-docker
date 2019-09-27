# phlax/glance
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    glance

CMD ["/usr/bin/python3", "/usr/bin/glance-registry", "--config-file=/etc/glance/glance-registry.conf"]
