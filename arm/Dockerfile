FROM hypriot/rpi-alpine:3.6
MAINTAINER Erik de Vries <docker@erikdevries.nl>

RUN apk -U update && \
    apk -U upgrade && \
    apk -U add \
        git \
        python \
        py-openssl \
        py-lxml \
    && \
    git clone --depth 1 https://github.com/CouchPotato/CouchPotatoServer.git /CouchPotato && \
    rm -rf /tmp/src && \
    rm -rf /var/cache/apk/*

VOLUME ["/config", "/data", "/downloads", "/movies"]

COPY ./entrypoint.sh /entrypoint.sh

EXPOSE 5050

ENTRYPOINT ["/bin/sh", "/entrypoint.sh"]
