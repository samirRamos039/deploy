# Base image
FROM node:14-alpine

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application
COPY . .

# Build the application
RUN npm run build

# Production image, copy only the necessary files
FROM nginx:1.19-alpine

# Set working directory
WORKDIR /usr/share/nginx/html

# Copy Vue.js application files from the node image
COPY --from=0 /app/dist/ /usr/share/nginx/html/

# Copy nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf