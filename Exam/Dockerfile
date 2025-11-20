FROM node:18 AS frontend-build
WORKDIR /app/client
COPY client/package*.json ./
RUN npm install
COPY client/ .
RUN npm run build

FROM node:18 AS backend
WORKDIR /app/server
COPY server/package*.json ./
RUN npm install
COPY server/ .
COPY --from=frontend-build /app/client/build ./public
EXPOSE 5000
CMD ["npm", "start"]
