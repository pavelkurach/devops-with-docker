# before: 600MB
# after: 380MB

FROM ubuntu:20.04

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apt-get -y update && apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup_16.x | bash && \
    apt-get -y install nodejs && \
    npm install && npm run build && \
    npm install -g serve && \
    apt-get purge -y --auto-remove curl && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf node_modules && \
    adduser appuser && chown appuser .

USER appuser

CMD serve -s -l 5000 build