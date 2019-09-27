# phlax/keystone
#
# VERSION       0.0.1

ARG BUILD_FROM=phlax/openstack

# Root stage
FROM $BUILD_FROM

RUN apt install \
    --no-install-recommends -y -qq \
    -t buster-stein-backports \
    keystone

RUN chown -R keystone:keystone /etc/keystone

CMD ["wait-for-it", "mariadb:3306", "--", "/usr/bin/uwsgi_python37", "--http-socket", "[::]:5000", "--ini", "/etc/keystone/keystone-uwsgi.ini"]
