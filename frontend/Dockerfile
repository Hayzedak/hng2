# Frontend Dockerfile
FROM node:16 AS build

# Set working directory
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy application files
COPY . .

# Build the frontend application
RUN npm run build

# Production stage
FROM nginx:latest

# Copy built files to nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]

