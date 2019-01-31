# Set the base image to Ubuntu
from ubuntu

# File author / maintainer
MAINTAINER ardhi

# Update the repository and install Redis server
RUN apt-get update && apt-get install -y redis-server

# Expose Redis port 6379
EXPOSE 6379

# Run Redis Server
ENTRYPOINT ["/usr/bin/redis-server"]
