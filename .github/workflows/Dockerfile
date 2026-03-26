# Stage 1: Build
FROM node:20 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Stage 2: Run
FROM node:20-alpine

WORKDIR /app

COPY --from=builder /app .

EXPOSE 5000

CMD ["npm", "start"]
