# Use the official Node.js image as the base image
FROM node:18

# Set the working directory
WORKDIR /usr/src/app

# Set the MongoDB URL environment variable


# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Install nodemon globally

# Copy the rest of the application code
COPY . .



# Expose port 8000
EXPOSE 8000

# Command to run the app
CMD ["npm", "start"]
