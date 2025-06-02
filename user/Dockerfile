FROM node:20

# Optional environment variable for Instana or profiling
ENV INSTANA_AUTO_PROFILE=true

# Set working directory
WORKDIR /opt/server

# Install dependencies
COPY package*.json ./
RUN npm install --production

# Copy source code
COPY server.js ./

# Expose app port
EXPOSE 8080

# Use a non-root user if possible
USER node

# Start the app
CMD ["node", "server.js"]
