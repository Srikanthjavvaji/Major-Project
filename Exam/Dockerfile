FROM node:18

WORKDIR /app

# Copy backend
COPY server/package*.json ./server/
RUN cd server && npm install
COPY server ./server

# Expose backend port
EXPOSE 5000

# Start backend from correct path
CMD ["node", "server/src/index.js"]
