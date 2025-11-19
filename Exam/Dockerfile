FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# ---------------------------
# 1️⃣ Install and build frontend (React)
# ---------------------------
COPY client/package*.json ./client/
RUN cd client && npm install

# Install Vite (fix for "vite: not found")
RUN cd client && npm install vite

# Copy remaining frontend code
COPY client ./client

# Build React frontend
RUN cd client && npm run build

# ---------------------------
# 2️⃣ Install backend (Node.js)
# ---------------------------
COPY server/package*.json ./server/
RUN cd server && npm install

COPY server ./server

# ---------------------------
# 3️⃣ Move frontend build → backend/public
# ---------------------------
RUN mkdir -p server/public
RUN cp -r client/build/* server/public/

# ---------------------------
# 4️⃣ Expose both ports
# ---------------------------
EXPOSE 3000
EXPOSE 5000

# ---------------------------
# 5️⃣ Start backend (serves frontend too)
# ---------------------------
CMD ["node", "server/index.js"]
