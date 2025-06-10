# ----------------------------------
# Environment: Peppermint.sh
# ----------------------------------
FROM --platform=$TARGETOS/$TARGETARCH pepperlabs/peppermint:latest

LABEL author="Koen" maintainer="koen@kvdmr.nl"

RUN apt install curl ca-certificates fontconfig git openssl tar tzdata

RUN apt-get update && \
    apt-get install -y build-essential python3 nodejs npm

# UID 999 is the default pterodactyl user
RUN useradd -m -d /home/container container

USER container
ENV HOME=/home/container
ENV PM2_HOME=/home/container/.pm2
WORKDIR /home/container

# Install PM2 globally, again, to use the correct PM2_HOME path
RUN npm install -g pm2

COPY        --chown=container:container ../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
CMD         ["/entrypoint.sh"]