# Use the official Nginx image from the Docker Hub
FROM nginx:alpine

# Copy your Nginx configuration file into the container
COPY nginx.conf /etc/nginx/nginx.conf


# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]


# Expose the HTTP port
EXPOSE 80 443
