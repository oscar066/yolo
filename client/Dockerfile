# STAGE 1: Build the React Application
FROM node:18-alpine AS build

WORKDIR /app

# Copy package manifests and install all dependencies 
COPY package*.json ./
RUN npm install

# Copy the React source code
COPY . .

# Add NODE_OPTIONS to use the legacy OpenSSL provider for compatibility
RUN NODE_OPTIONS=--openssl-legacy-provider npm run build

# Serve the Production Build with Nginx
FROM nginx:1.23-alpine

# Copy ONLY the static build files from the previous stage into Nginx's web root
COPY --from=build /app/build /usr/share/nginx/html

# Add our custom Nginx config to handle React Router
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80


# The default Nginx command starts the server automatically
CMD ["nginx", "-g", "daemon off;"]