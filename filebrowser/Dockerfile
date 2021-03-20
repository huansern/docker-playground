FROM alpine:3.8

ARG UID=1000
ARG GID=1000

WORKDIR /tmp

RUN addgroup -g $GID browser && \
adduser -h /browser -D -u $UID -G browser browser && \
wget -O browser.tar.gz https://github.com/filebrowser/filebrowser/releases/download/v2.0.2/linux-amd64-filebrowser.tar.gz && \
tar xzf browser.tar.gz && \
mv filebrowser /usr/local/bin/ && \
rm *

USER browser

WORKDIR /browser

COPY --chown=browser:browser config.json .

RUN mkdir root branding

EXPOSE 8080

ENTRYPOINT [ "filebrowser" ]

CMD [ "-c", "config.json" ]