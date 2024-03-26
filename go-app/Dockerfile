# Use the official Go image as a build environment
FROM golang:1.17 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the Go application source code into the container
COPY . .

# Build the Go binary
RUN go build -o myapp .

# Use a minimal base image for the final image
FROM alpine:latest

# Set the working directory inside the container
WORKDIR /root/

# Copy the built binary from the build container into the final container
COPY --from=build /app/myapp .

# Command to run the Go application
CMD ["./myapp"]
