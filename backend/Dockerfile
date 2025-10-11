# Smallest official Node.js image available
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package manifests. 
# This layer is cached and only re-runs if package.json changes.
COPY package*.json ./

# Install ONLY production dependencies to keep the image small
RUN npm install --omit=dev

# Copy the rest of the application source code
COPY . .

# Listens on port 5000
EXPOSE 5000

# The command to run when the container starts
CMD [ "node", "server.js" ]