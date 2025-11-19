FROM node:18

WORKDIR /app

# Copy ONLY package.json (NOT node_modules)
COPY server/package*.json ./server/

# Install backend dependencies (Linux binaries)
RUN cd server && npm install --build-from-source

# Copy backend source code (skip node_modules)
COPY server ./server

EXPOSE 5000

CMD ["node", "server/src/index.js"]
