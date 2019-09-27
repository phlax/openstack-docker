# phlax/neutron-server
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    neutron-common
RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    neutron-server

CMD ["wait-for-it", "neutron-api:9696", "--", "/usr/bin/python3", "/usr/bin/neutron-rpc-server", "--config-file=/etc/neutron/neutron.conf", "--config-dir=/etc/neutron/server.conf.d", "--config-file=/etc/neutron/plugins/ml2/ml2_conf.ini"]
