# Stage 1: Build Angular application
FROM node:18 AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Angular application
RUN npm run build --prod

# Stage 2: Serve Angular application with NGINX
FROM nginx:alpine

# Copy the built application from the previous stage
COPY --from=build /app/dist/<your-angular-app-name> /usr/share/nginx/html

# Copy a default NGINX configuration (optional, use if you want custom NGINX behavior)
# COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start NGINX server
CMD ["nginx", "-g", "daemon off;"]
