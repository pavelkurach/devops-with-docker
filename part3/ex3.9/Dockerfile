# before: 679MB
# after: 17.7MB

FROM golang:1.20-alpine3.17 as server-build

WORKDIR /usr/src/app

# pre-copy/cache go.mod for pre-downloading dependencies and only redownloading them in subsequent builds if they change
COPY go.mod go.sum ./
RUN go mod download && go mod verify

COPY . .

RUN go build 


FROM scratch

ENV PORT=8000

EXPOSE 8000

WORKDIR /usr/src/app

COPY --from=server-build /usr/src/app/server /usr/src/app/server

CMD ["./server"]