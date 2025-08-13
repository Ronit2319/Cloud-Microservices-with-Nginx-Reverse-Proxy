FROM golang:1.22-alpine
RUN apk add --no-cache curl
WORKDIR /app
COPY . .
RUN go build -o main main.go
EXPOSE 8001
CMD ["./main"]
