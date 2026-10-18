# --- Build Stage ---
FROM node:18-alpine AS build

WORKDIR /app

# Copy dependency files
COPY package.json package-lock.json ./
RUN npm install

# Copy all frontend source code
COPY . .

# Build production assets
RUN npm run build


# --- Serve Stage ---
FROM nginx:alpine

# Copy built files from the build stage into Nginx's public directory
COPY --from=build /app/dist /usr/share/nginx/html

# Expose Nginx default port
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]

#Well, I don't think I did mine right. You can add information, but you can't add the recipe. I'm writing this comment here because it's a frontend issue. 
#My backend has worked fine far as I can tell.
