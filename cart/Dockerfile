FROM node:18

ENV NODE_ENV=production
ENV INSTANA_AUTO_PROFILE=true

WORKDIR /opt/server

# Install dependencies
COPY package*.json ./
RUN npm install --omit=dev

# Copy app code
COPY server.js ./

EXPOSE 8080

CMD ["node", "server.js"]
