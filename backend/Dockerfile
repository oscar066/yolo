# Use a modern, secure, and alpine-based LTS Node.js version for the build stage
FROM node:18-alpine AS build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

#Add multi-stage build

# Use a recent, stable version of Alpine Linux
FROM alpine:3.19

WORKDIR /app

RUN apk update && apk add --update nodejs npm

# Copy the built application from the 'build' stage
COPY --from=build /usr/src/app /app

# Expose the port the app runs on
EXPOSE 5000

# Define the command to run your app
CMD ["node", "server.js"]