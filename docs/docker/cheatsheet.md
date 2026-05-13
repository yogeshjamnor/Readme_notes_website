# Docker Cheatsheet

Quick reference for Docker and Docker Compose.

## Container Lifecycle

| Command | Description |
| :--- | :--- |
| `run` | Create and start a container |
| `start` | Start a stopped container |
| `stop` | Stop a running container |
| `restart` | Stop and start a container |
| `pause` | Suspend processes in a container |
| `unpause` | Unsuspend processes |
| `kill` | Kill a running container |

## Information and Monitoring

```bash
docker version # Show version
docker info    # System-wide information
docker ps      # List running containers
docker stats   # Container resource usage
docker top     # Display processes in container
docker inspect # Low-level info on objects
```
## Volumes and Networks

```bash
docker volume ls      # List volumes
docker volume create  # Create volume
docker network ls     # List networks
docker network create # Create network
```
## Docker Compose Quick Ref

```bash
docker compose up -d    # Start in background
docker compose ps       # List containers
docker compose logs -f  # Tail logs
docker compose down     # Stop and remove
docker compose exec <svc> <cmd> # Run command in service
```
## Useful Shortcuts

- `docker rm -f $(docker ps -aq)`: Remove all containers.
- `docker rmi $(docker images -q)`: Remove all images.
- `docker system prune -a --volumes`: Nuclear cleanup (removes everything unused).


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
