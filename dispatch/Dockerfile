FROM golang:1.21

WORKDIR /app

COPY . .

RUN go mod init dispatch \
 && go get github.com/instana/go-sensor@v1.66.0 \
 && go mod tidy \
 && go build -o dispatch ./...

CMD ["./dispatch"]
