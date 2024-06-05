# Use a Node.js base image
FROM node:14

# Set working directory
WORKDIR /app/53832_backend/Auth

# Copy package.json and package-lock.json to install dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port on which the service will run  ---- 53832+2000
EXPOSE 55832

# Command to run the service
CMD ["npm", "start"]
