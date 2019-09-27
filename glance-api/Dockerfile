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

env PYTHONWARNINGS="ignore::DeprecationWarning:alembic"
CMD ["/usr/bin/uwsgi_python37", "--http-socket", "[::]:9292", "--ini", "/etc/glance/glance-api-uwsgi.ini"]
