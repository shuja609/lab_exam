FROM node:slim

# base image for the API Gateway service
# Set environment variables
ENV NODE_ENV=production

# Add metadata labels
LABEL maintainer="CafeManagementSystem"
LABEL description="Menu Service"
LABEL version="1.0"

# Update and install any required system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*


# Set the working directory in the container
WORKDIR /menu-services

# Copy package files first for better caching
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy app source code
COPY . .

# Expose API Gateway port
EXPOSE 3001

# Start the service
CMD ["node", "index.js"]
