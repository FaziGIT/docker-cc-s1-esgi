FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

FROM node:18-alpine AS production

WORKDIR /app

COPY package*.json ./
RUN npm install --only=production

COPY --from=build /app/src ./src
COPY --from=build /app/package.json .

EXPOSE 3001

CMD ["npm", "start"]
