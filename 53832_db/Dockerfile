# Use the official MongoDB image from Docker Hub
FROM mongo:latest

# Set the data directory as a volume to persist data
VOLUME /data/db

# Expose MongoDB default port - valid port range for MongoDB is typically between 27017 and 27019 so roll no not used
EXPOSE 27017

# Command to run MongoDB server
CMD ["mongod"]


