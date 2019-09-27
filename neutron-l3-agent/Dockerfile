# phlax/neutron-l3-agent
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
    neutron-l3-agent


CMD ["wait-for-it", "neutron-api:9696", "--", "/usr/bin/python3", "/usr/bin/neutron-l3-agent", "--config-file=/etc/neutron/neutron.conf", "--config-dir=/etc/neutron/agent.conf.d", "--config-file=/etc/neutron/l3_agent.ini"]
