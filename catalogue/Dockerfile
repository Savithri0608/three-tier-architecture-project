FROM node:18

# Set environment variable for Instana
ENV INSTANA_AUTO_PROFILE=true

# Set the working directory
WORKDIR /opt/server

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY server.js ./

# Expose the application port
EXPOSE 8080

# Run the application
CMD ["node", "server.js"]
