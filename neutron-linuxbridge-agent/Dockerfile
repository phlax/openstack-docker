# phlax/neutron-linuxbridge-agent
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
    neutron-linuxbridge-agent

CMD ["wait-for-it", "neutron-api:9696", "--", "/usr/bin/python3", "/usr/bin/neutron-linuxbridge-agent", "--config-file=/etc/neutron/neutron.conf", "--config-file=/etc/neutron/plugins/ml2/ml2_conf.ini", "--config-file=/etc/neutron/plugins/ml2/linuxbridge_agent.ini"]
