FROM node:18

WORKDIR /app

# ----------------------------------
# 1. Copy backend dependency files
# ----------------------------------
COPY server/package*.json ./server/

# Install backend dependencies (Linux-compatible bcrypt)
RUN cd server && npm install --build-from-source

# ----------------------------------
# 2. Copy backend application code
# ----------------------------------
COPY server ./server

# ----------------------------------
# 3. Expose backend port
# ----------------------------------
EXPOSE 5000

# ----------------------------------
# 4. Start backend server
# ----------------------------------
CMD ["node", "server/src/index.js"]
