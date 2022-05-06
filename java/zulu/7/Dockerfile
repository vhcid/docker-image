FROM --platform=$TARGETOS/$TARGETARCH debian:bullseye-slim

LABEL author="andhra21231" maintainer="support@pelajar.social"

RUN useradd -d /home/container -m container

RUN apt-get -y update
RUN apt-get -yq install gnupg curl

RUN apt-key adv \
  --keyserver hkp://keyserver.ubuntu.com:80 \
  --recv-keys 0xB1998361219BD9C9
RUN curl -O https://cdn.azul.com/zulu/bin/zulu-repo_1.0.0-3_all.deb
RUN apt-get -y install ./zulu-repo_1.0.0-3_all.deb
RUN apt-get -y update

RUN apt-get -y install zulu7-jdk-headless

USER container
ENV USER=container WORKDIR=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]