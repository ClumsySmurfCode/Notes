# Use Alpine Linux as the base image
FROM alpine:latest
# Remove unnecessary packages
RUN apk --no-cache del curl wget \
    && rm -rf /var/cache/apk/*
