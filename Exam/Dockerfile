############### FRONTEND BUILD STAGE ###############
FROM node:18 AS frontend-build
WORKDIR /app/client

COPY client/package*.json ./
RUN npm install

COPY client/ ./
RUN npm run build

############### BACKEND STAGE ###############
FROM node:18 AS backend
WORKDIR /app/server

RUN apt-get update && apt-get install -y python3 make g++ && apt-get clean

COPY server/package*.json ./
RUN npm install

COPY server/ ./

RUN npm rebuild bcrypt --build-from-source || true

COPY --from=frontend-build /app/client/dist ./public

EXPOSE 5000
CMD ["npm", "start"]
