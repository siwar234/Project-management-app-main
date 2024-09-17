# Step 1: Build the React app
FROM node:16 as build

WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps

  # Copy the rest of the application code
    COPY . .
    
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
