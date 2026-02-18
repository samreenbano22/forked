# Node version-package we are using to build the application
FROM node:22-alpine AS builder

# Set up the work directory
WORKDIR /app


# Copy the package files
COPY . .


# run the install command
RUN npm ci --only=production
# copy the entire code base


# run the build command
RUN npm run build

# something different  
FROM nginx:alpine AS production

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
