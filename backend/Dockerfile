FROM golang:1.25-alpine AS builder

WORKDIR /app
COPY main.go .

RUN go build -o backend main.go

FROM alpine

RUN addgroup -g 1000 -S application && adduser -u 1000 -S racus -G application

WORKDIR /app

COPY --from=builder --chown=racus:application /app/backend .

EXPOSE 8080

USER racus

CMD ["./backend"]