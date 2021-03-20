FROM debian:stretch-slim

ARG UID=1000
ARG GID=1000

RUN groupadd -g $GID deluge && \
useradd -d /deluge -u $UID -g deluge -s /bin/bash deluge && \
apt-get update && \
apt-get install --no-install-recommends -y supervisor deluged deluge-console deluge-web procps && \
mkdir /deluge && \
chown -R deluge:deluge /deluge && \
rm -rf /var/lib/apt/lists/*

COPY supervisord.conf /etc/supervisor/conf.d/deluge.conf

EXPOSE 8112 58864

WORKDIR /etc

CMD [ "supervisord" ]
