FROM ubuntu:20.04

ENV REACT_APP_BACKEND_URL=http://127.0.0.1:8000

EXPOSE 5000

WORKDIR /usr/src/app

RUN apt-get -y update && apt-get -y install curl

COPY . .

RUN curl -sL https://deb.nodesource.com/setup_16.x | bash \
    && apt-get -y install nodejs

RUN npm install && npm run build

RUN npm install -g serve

CMD serve -s -l 5000 build