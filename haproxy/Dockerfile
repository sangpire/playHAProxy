FROM haproxy:1.8.31-alpine3.16

LABEL maintainer="Meik Minks <mminks@inoxio.de>"

RUN set -exo pipefail \
    && apk add --no-cache \
        rsyslog \
    && mkdir -p /etc/rsyslog.d \
    && touch /var/log/haproxy.log \
    && ln -sf /dev/stdout /var/log/haproxy.log

COPY docker-entrypoint.sh /
COPY rsyslog.conf /etc/rsyslog.d/

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["-f", "/usr/local/etc/haproxy/haproxy.cfg"]
