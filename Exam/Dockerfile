FROM node:18

WORKDIR /app

# Copy backend package files
COPY server/package*.json ./server/
RUN cd server && npm install --build-from-source

# Copy backend source code (NOT node_modules)
COPY server ./server

EXPOSE 5000

CMD ["node", "server/src/index.js"]
