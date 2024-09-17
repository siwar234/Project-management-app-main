# Use an official Node.js runtime as a parent image for the build stage
FROM node:16-alpine AS build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy only package.json and package-lock.json first to leverage Docker cache for npm install
COPY package*.json ./

# Install dependencies
RUN npm install --legacy-peer-deps

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Use a lightweight Nginx image to serve the built app
FROM nginx:alpine

# Remove default nginx website
RUN rm -rf /usr/share/nginx/html/*

# Copy the built React app from the build stage to Nginx's default directory
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose port 80 for HTTP traffic (Nginx default)
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
