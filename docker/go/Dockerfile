# Base image
FROM golang:1.19rc2-alpine3.16 AS go-base

WORKDIR /go/hello-app/src

COPY ./hello.go .
RUN go mod init fullcycle/hello-go
RUN go build -o ../build/bin/hello .

# Run from scratch image
FROM scratch

WORKDIR /app

COPY --from=go-base /go/hello-app/build/bin/hello .

CMD ["./hello"]