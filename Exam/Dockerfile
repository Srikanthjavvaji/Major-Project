# ------------------------------------------------------
# 1️⃣ FRONTEND BUILD (React + Vite)
# ------------------------------------------------------
FROM node:18 AS frontend-build

WORKDIR /app/client

# Copy only essential frontend files first
COPY client/package*.json ./
RUN npm install

# Copy full frontend project
COPY client/ ./

# Build frontend (creates /dist)
RUN npm run build


# ------------------------------------------------------
# 2️⃣ BACKEND BUILD (Node.js)
# ------------------------------------------------------
FROM node:18 AS backend-build

WORKDIR /app/server

COPY server/package*.json ./
RUN npm install

COPY server/ ./


# ------------------------------------------------------
# 3️⃣ RUNTIME CONTAINER
# ------------------------------------------------------
FROM node:18

WORKDIR /app/server

# Copy backend code
COPY --from=backend-build /app/server ./

# Copy built frontend → backend/public
RUN mkdir -p public
COPY --from=frontend-build /app/client/dist ./public/

# Expose ports
EXPOSE 5000
EXPOSE 3000

# Start the backend (serves frontend from /public)
CMD ["node", "index.js"]
