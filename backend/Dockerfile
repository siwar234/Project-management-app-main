# Use the official Node.js image as the base image
FROM node:16

# Set the working directory
WORKDIR /usr/src/app

# Set the MongoDB URL environment variable
ENV MONGO_URL mongodb://mongodb-container:27017/projectmanagement


# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Install nodemon globally

# Copy the rest of the application code
COPY . .


# Build the React app
RUN npm run build

# Use a lightweight web server image to serve the built app
FROM nginx:alpine

# Copy the built React app from the build stage
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose the port on which nginx will run
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
