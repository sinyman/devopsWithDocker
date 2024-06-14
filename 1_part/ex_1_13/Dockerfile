FROM golang:1.16

WORKDIR /usr/src/app

# Copying project files
COPY . .

# Building project
RUN go build

# Expose port
EXPOSE 8080

# Start server
CMD ["./server"]
