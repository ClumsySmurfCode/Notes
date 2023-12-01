# Use Alpine Linux as the base image
-- 
Creating a minified Linux image for Docker typically involves starting with a base image and then removing unnecessary components to reduce the image size. Below is a basic example using Alpine Linux, which is known for its small size. Make sure you have Docker installed on your system.

"FROM alpine:latest"


# Remove unnecessary packages
RUN apk --no-cache del curl wget \
    && rm -rf /var/cache/apk/*
