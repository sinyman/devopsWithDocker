
FROM golang:1.16

WORKDIR /usr/src/app

# Copying project files
COPY . .

# Expose port
EXPOSE 8080

# Setting up environment vars
ENV REQUEST_ORIGIN=http://localhost:5000

# Building project
RUN go build

# Start server
CMD ["./server"]
