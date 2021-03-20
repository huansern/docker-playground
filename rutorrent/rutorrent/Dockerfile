FROM php:5.6.40-fpm-alpine3.8

ARG GID=1000

RUN addgroup -g $GID rtorrent && \
addgroup www-data rtorrent && \
mkdir /rutorrent /rtorrent && \
chown -R www-data:www-data /rutorrent

USER www-data

WORKDIR /rutorrent

RUN wget -O rutorrent.tar.gz https://github.com/Novik/ruTorrent/archive/v3.8.tar.gz && \
tar xzf rutorrent.tar.gz --strip-components=1 && \
mkdir tmp && \
mv plugins/* tmp && \
mv tmp/_getdir plugins && \
mv tmp/_noty2 plugins && \
mv tmp/chunks plugins && \
mv tmp/cpuload plugins && \
mv tmp/diskspace plugins && \
mv tmp/geoip plugins && \
mv tmp/ipad plugins && \
mv tmp/seedingtime plugins && \
mv tmp/show_peers_like_wtorrent plugins && \
mv tmp/throttle plugins && \
rm rutorrent.tar.gz LICENSE.md README.md .gitignore && \
rm -rf tmp && \
rm conf/config.php

COPY config.php conf/config.php