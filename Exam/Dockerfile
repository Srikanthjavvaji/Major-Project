FROM node:18

WORKDIR /app

# ---------------------------
# 1️⃣ Copy backend
# ---------------------------
COPY server/package*.json ./server/
RUN cd server && npm install
COPY server ./server

# ---------------------------
# 2️⃣ Copy pre-built frontend (dist folder)
# ---------------------------
RUN mkdir -p server/public
COPY client/dist ./server/public/

# ---------------------------
# 3️⃣ Expose ports
# ---------------------------
EXPOSE 5000
EXPOSE 3000

# ---------------------------
# 4️⃣ Start backend server
# ---------------------------
CMD ["node", "server/index.js"]
