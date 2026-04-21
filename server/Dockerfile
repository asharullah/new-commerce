FROM node:20-alpine

# Avoid unnecessary OS upgrades (keep image stable)
RUN apk add --no-cache dumb-init

WORKDIR /app

# Install dependencies first (better caching)
COPY package*.json ./

RUN npm ci --omit=dev

# Then copy app source
COPY . .

EXPOSE 3001

CMD ["dumb-init", "node", "app.js"]
