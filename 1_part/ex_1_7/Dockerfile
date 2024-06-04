# Getting base image
FROM ubuntu:22.04

# Set /usr/src/app as our working directory.
WORKDIR /usr/src/app

# Copy the script into the container
COPY script.sh .

# Making script executable
RUN chmod +x script.sh

# Refreshing package repos and installing curl
RUN apt update && apt install curl -y

# Running script
CMD ./script.sh
