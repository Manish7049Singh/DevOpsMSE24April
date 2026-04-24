# Use node:18-alpine as the base image
FROM node:18-alpine

# Set /app as the working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy application files
COPY . .

# Expose port 8080
EXPOSE 8080

# Start the application using node index.js
CMD ["node", "index.js"]
