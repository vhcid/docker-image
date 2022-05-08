FROM --platform=$TARGETOS/$TARGETARCH node:12-bullseye-slim

LABEL author="andhra21231" maintainer="support@pelajar.social"

RUN apt update && apt upgrade -y
RUN apt -y install ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool
RUN npm -g install npm@latest
RUN npm -g install yarn@latest
RUN useradd -m -d /home/container container

USER container
ENV USER=container WORKDIR=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
