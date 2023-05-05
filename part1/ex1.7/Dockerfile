FROM ubuntu:20.04

WORKDIR /usr/src/app

COPY curler.sh .

RUN apt-get -y update && apt-get -y install curl && chmod +x ./curler.sh

CMD ./curler.sh