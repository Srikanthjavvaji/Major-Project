# ------------------------------------------------------
# 1️⃣ FRONTEND BUILD STAGE (uses full node image)
# ------------------------------------------------------
FROM node:18 AS frontend-build
WORKDIR /app

COPY client/package*.json ./client/
RUN cd client && npm install

COPY client ./client
RUN cd client && npm run build


# ------------------------------------------------------
# 2️⃣ BACKEND BUILD STAGE
# ------------------------------------------------------
FROM node:18
WORKDIR /app

COPY server/package*.json ./server/
RUN cd server && npm install

COPY server ./server

# Copy frontend build → backend/public
RUN mkdir -p server/public
COPY --from=frontend-build /app/client/build ./server/public/

# Expose ports
EXPOSE 3000
EXPOSE 5000

# Start backend
CMD ["node", "server/index.js"]
