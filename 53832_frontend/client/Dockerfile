
# Use a Node.js base image
FROM node:14

# Set working directory
WORKDIR /app/53832_frontend/client

# Copy package.json and package-lock.json to install dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Expose the port on which the service will run   ---- roll number 3832 and added 5 in front
EXPOSE 53832

# Command to run the service
CMD ["npm", "start"]
