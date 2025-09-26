# Docker Cheat Sheet

# Build an image from a Dockerfile (the -t flag tags the image with a name)
docker build -t myapp .

# Run a container from an image (with port mapping: host:container)
docker run -d -p 8080:8080 --name mycontainer myapp

# List running containers
docker ps

# List all containers (including stopped ones)
docker ps -a

# View logs of a running container
docker logs -f mycontainer

# Execute a shell inside a running container
docker exec -it mycontainer sh

# Stop a running container
docker stop mycontainer

# Start a stopped container
docker start mycontainer

# Remove a container
docker rm mycontainer

# Remove an image
docker rmi myapp

# Clean up unused images, containers, and networks
docker system prune -f
