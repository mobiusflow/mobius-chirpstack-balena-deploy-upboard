FROM postgres:14-alpine

RUN mkdir -p /docker-entrypoint-initdb.d
COPY ./initdb/001-init-chirpstack.sh /docker-entrypoint-initdb.d/001-init-chirpstack.sh
COPY ./initdb/002-chirpstack_extensions.sh /docker-entrypoint-initdb.d/002-chirpstack_extensions.sh
