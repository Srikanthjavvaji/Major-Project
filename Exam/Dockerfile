FROM node:18

WORKDIR /app

# Copy backend files
COPY server/package*.json ./server/
RUN cd server && npm install
COPY server ./server

# Expose backend port
EXPOSE 5000

# Start backend
CMD ["node", "server/index.js"]
