# Use the official Node.js image as a build environment
FROM node:14-alpine AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json files into the container
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy the entire application source code into the container
COPY . .

# Build the Next.js application
RUN npm run build

# Use a minimal base image for the final image
FROM nginx:alpine

# Copy the built Next.js application from the build container into the final container
COPY --from=build /app/out /usr/share/nginx/html

# Expose port 80
EXPOSE 80
