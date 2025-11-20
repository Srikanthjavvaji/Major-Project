FROM node:18 AS frontend-build
WORKDIR /app/frontend

COPY package*.json ./
RUN npm install

COPY . .
RUN npx vite build

FROM node:18 AS backend
WORKDIR /app/server

COPY server/package*.json ./
RUN npm install

COPY server/ .

COPY --from=frontend-build /app/frontend/dist ./public

EXPOSE 5000
CMD ["npm", "start"]
