# before: 290MB
# after: 73.9MB

FROM node:16-alpine3.17 as frontend-build

WORKDIR /usr/src/app

COPY . .

RUN apk add --no-cache curl bash && \
    curl -sL https://deb.nodesource.com/setup_16.x && \
    npm install && npm run build 



FROM alpine:latest

EXPOSE 5000

WORKDIR /usr/src/app

RUN apk add --no-cache nodejs npm ca-certificates && npm install -g serve && \
    adduser -S appuser && chown appuser .

COPY --from=frontend-build /usr/src/app/build/ /usr/src/app/build/

USER appuser

CMD serve -s -l 5000 build