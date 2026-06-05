FROM golang:1.26-alpine AS builder
WORKDIR /app
COPY go.mod .
COPY . .
RUN go mod tidy
RUN go build -o auth-service .

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/auth-service ./
EXPOSE 8001
CMD ["./auth-service"]
