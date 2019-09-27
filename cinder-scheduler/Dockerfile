# phlax/cinder-scheduler
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    cinder-scheduler

CMD ["wait-for-it", "rabbitmq:5672", "--", "/usr/bin/python3", "/usr/bin/cinder-scheduler", "--config-file=/etc/cinder/cinder.conf"]
