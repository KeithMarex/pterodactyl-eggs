# ----------------------------------
# Environment: Peppermint.sh
# ----------------------------------
FROM --platform=$TARGETOS/$TARGETARCH pepperlabs/peppermint:latest

LABEL author="Koen" maintainer="koen@kvdmr.nl"

# UID 999 is the default pterodactyl user
RUN adduser -D -h /home/container container

RUN apt install curl ca-certificates fontconfig git openssl tar tzdata

USER container
ENV HOME=/home/container
WORKDIR /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT  ["/sbin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]