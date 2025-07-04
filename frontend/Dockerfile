# Stage 1: Build the React application
FROM node:22-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (or yarn.lock) to install dependencies
# This step is done early to leverage Docker's cache.
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application code into the container
COPY . /app

# Build the React app for production
# This command runs the 'build' script defined in your package.json,
# which typically creates an optimized, static build in the 'build' folder.
RUN npm run build

# Stage 2: Serve the built application with Nginx
# Use a very lightweight Nginx image based on Alpine Linux.
FROM nginx:alpine

# Remove default Nginx configuration to replace it with our custom one
RUN rm /etc/nginx/conf.d/default.conf

# Copy the custom Nginx configuration file from your frontend/ directory
# This file is essential for Single Page Applications (SPAs) like React.
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy the built React application from the 'builder' stage to Nginx's web root
# The 'build' folder is created by 'npm run build' in the previous stage.
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80 (default HTTP port for Nginx)
EXPOSE 80

# Command to start Nginx in the foreground
# 'daemon off;' is necessary when running Nginx in a Docker container.
CMD ["nginx", "-g", "daemon off;"]