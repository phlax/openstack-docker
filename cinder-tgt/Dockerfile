# phlax/cinder-tgt
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    tgt

CMD ["/usr/sbin/tgtd", "-f"]
