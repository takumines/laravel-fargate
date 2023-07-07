# Define the Node.js build stage
FROM node:16-buster AS build-stage

WORKDIR /app

# Nginx stage
FROM nginx:1.20-alpine

# Set timezone
ENV TZ=UTC

# Update apk and install dependencies
RUN apk update && \
  apk add --update --no-cache --virtual=.build-dependencies g++

# Install Node.js and npm
RUN apk add --update nodejs npm

# Copy Nginx configuration files
COPY ./infra/docker/nginx/*.conf /etc/nginx/conf.d/

COPY ./backend/public /work/backend/public

WORKDIR /work/backend
