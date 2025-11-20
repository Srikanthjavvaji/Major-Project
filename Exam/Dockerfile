FROM node:18 AS frontend-build
WORKDIR /app/client

ENV NODE_ENV=development
ENV NPM_CONFIG_PRODUCTION=false

COPY client/package*.json ./
RUN npm install

COPY client/ ./
RUN npm run build


FROM node:18 AS backend
WORKDIR /app/server

ENV NODE_ENV=development
ENV NPM_CONFIG_PRODUCTION=false

COPY server/package*.json ./
RUN npm install
RUN npm rebuild bcrypt --build-from-source || npm install bcrypt

COPY server/ ./
COPY --from=frontend-build /app/client/dist ./public

EXPOSE 5000
CMD ["npm", "start"]
