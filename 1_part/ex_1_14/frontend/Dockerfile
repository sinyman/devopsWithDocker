
FROM ubuntu:22.04

WORKDIR /usr/src/app

COPY . .

# Expose app running on port 5000
EXPOSE 5000

# Setting environment vars
ENV REACT_APP_BACKEND_URL=http://localhost:8080

# Updating package repos and installing curl
RUN apt update && apt install -y curl

# Installing NodeJS and npm
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt install -y nodejs

# Installing packages
RUN npm install && npm install -g serve

# Building the static files
RUN npm run build

# Running the container
CMD ["serve", "-s", "-l", "5000", "build"]

