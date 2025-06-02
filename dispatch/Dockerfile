FROM golang:1.17

WORKDIR /app

# Copy Go module files first for better caching
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the rest of the source code
COPY . .

# Build the binary
RUN go build -o dispatch

# Run the binary
CMD ["./dispatch"]
