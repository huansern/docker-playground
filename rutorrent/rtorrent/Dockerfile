FROM alpine:latest

ARG UID=1000
ARG GID=1000

RUN addgroup -g $GID rtorrent && \
adduser -h /rtorrent -D -u $UID -G rtorrent rtorrent && \
apk add --no-cache --update rtorrent

COPY --chown=rtorrent:rtorrent .rtorrent.rc /rtorrent/

USER rtorrent

RUN mkdir ~/watch ~/downloads ~/log ~/.session

EXPOSE 5000 6881/udp 49164

CMD [ "rtorrent" ]