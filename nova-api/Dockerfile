# phlax/nova-api
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
    nova-api

CMD ["wait-for-it", "rabbitmq:5672", "--", "wait-for-it", "mariadb:3306", "--", "/usr/bin/python3", "/usr/bin/nova-api", "--config-file=/etc/nova/nova.conf"]
