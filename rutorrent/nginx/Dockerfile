FROM nginx:alpine

WORKDIR /etc/nginx/conf.d

RUN rm default.conf

COPY rutorrent.conf .

RUN mkdir /rutorrent

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
chown -R nginx:nginx /rutorrent