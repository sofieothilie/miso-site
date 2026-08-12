FROM node:22-alpine

WORKDIR /app

# Install deps first (better layer caching)
COPY package*.json ./
RUN npm ci

# Copy the rest of the app and build
COPY . .
RUN npm run build

EXPOSE 3000

# Use Next's own server
CMD ["npm", "start"]