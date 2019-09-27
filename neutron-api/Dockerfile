# phlax/neutron-api
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

CMD ["wait-for-it", "rabbitmq:5672", "--", "wait-for-it", "keystone:5000", "--", "/usr/bin/uwsgi_python37", "--http-socket", "[::]:9696", "--ini", "/etc/neutron/neutron-api-uwsgi.ini", "--pyargv", "--config-dir=/etc/neutron/server.conf.d --config-file=/etc/neutron/neutron.conf --config-file=/etc/neutron/plugins/ml2/ml2_conf.ini"]
