# before: 1.18GB
# after: 679MB

FROM golang:1.20-alpine3.17

ENV PORT=8000

EXPOSE 8000

WORKDIR /usr/src/app

# pre-copy/cache go.mod for pre-downloading dependencies and only redownloading them in subsequent builds if they change
COPY go.mod go.sum ./
RUN go mod download && go mod verify && \
    adduser -S appuser && chown appuser .

COPY . .

RUN go build 

USER appuser

CMD ["./server"]