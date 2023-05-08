# before: 380MB
# after: 290MB

FROM node:16-alpine3.17

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apk add --no-cache curl ca-certificates bash && \
    curl -sL https://deb.nodesource.com/setup_16.x && \
    npm install && npm run build && \
    npm install -g serve && \
    apk del curl && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf node_modules && \
    adduser -S appuser && chown appuser .

USER appuser

CMD serve -s -l 5000 build