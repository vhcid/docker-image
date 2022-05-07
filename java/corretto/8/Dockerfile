FROM --platform=$TARGETOS/$TARGETARCH debian:bullseye-slim

LABEL author="andhra21231" maintainer="support@pelajar.social"

RUN useradd -d /home/container -m container

RUN apt-get -y update
RUN apt-get -y upgrade
RUN apt-get install -y curl ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2 libfreetype6 wget apt-transport-https gnupg2 apt-utils software-properties-common procps

RUN wget -O- https://apt.corretto.aws/corretto.key | sudo apt-key add - 
RUN add-apt-repository 'deb https://apt.corretto.aws stable main'
RUN apt-get -y update
RUN apt-get -y upgrade

RUN apt-get install -y java-1.8.0-amazon-corretto-jdk

USER container
ENV USER=container WORKDIR=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]