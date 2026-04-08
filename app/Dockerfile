FROM node:18-alpine

# Create app directory
WORKDIR /app

# Copy files
COPY package*.json ./
RUN npm install

COPY . .

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

EXPOSE 3000

CMD ["node", "index.js"]