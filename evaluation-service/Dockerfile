FROM golang:1.26-alpine AS builder
WORKDIR /app
COPY go.mod .
COPY . .
RUN go mod tidy
RUN go build -o evaluation-service .

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/evaluation-service ./
EXPOSE 8004
CMD ["./evaluation-service"]
