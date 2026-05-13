# Docker CLI Commands

Essential commands for managing images, containers, and volumes.

## Image Commands

```bash
# Build an image
docker build -t my-app .

# List images
docker images

# Remove an image
docker rmi <image_id>

# Pull image from registry
docker pull node:latest
```
## Container Commands

```bash
# Run a container
docker run -p 3000:3000 --name my-running-app my-app

# Run in detached mode (background)
docker run -d my-app

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container_id>

# Remove a container
docker rm <container_id>

# View logs
docker logs -f <container_id>

# Execute command inside container
docker exec -it <container_id> sh
```
## Docker Compose Commands

```bash
# Start all services
docker compose up -d

# Stop and remove services
docker compose down

# View logs for all services
docker compose logs -f

# Rebuild images
docker compose build
```
## Maintenance Commands

```bash
# Remove unused data (images, containers, networks)
docker system prune

# List volumes
docker volume ls
```
## Useful CLI Shortcuts

- `docker stats`: Display a live stream of container(s) resource usage statistics.
- `docker inspect <id>`: Return low-level information on Docker objects.


## Code Examples

### Multi‑stage Dockerfile (smaller images)
```dockerfile
# build stage
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# runtime stage
FROM node:20-alpine
WORKDIR /app
ENV NODE_ENV=production
COPY --from=build /app/dist ./dist
COPY --from=build /app/package*.json ./
RUN npm ci --omit=dev
CMD ["node", "dist/index.js"]
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
