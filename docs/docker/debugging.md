# Debugging Docker

Tools and techniques for troubleshooting Docker containers.

## Viewing Logs

The most common way to debug is by checking container logs.

```bash
docker logs <container_id>

# Follow logs in real-time
docker logs -f <container_id>

# View last 100 lines
docker logs --tail 100 <container_id>
```
## Interactive Shell

Access the terminal inside a running container.

```bash
docker exec -it <container_id> /bin/sh
# or /bin/bash if available
```
## Inspecting Container State

```bash
# View network, volumes, and env vars
docker inspect <container_id>

# View resource usage (CPU, Memory)
docker stats
```
## Common Errors

### 1. `Conflict: name already in use`
- **Cause**: Trying to start a container with a name that already exists.
- **Fix**: Remove the old container `docker rm <name>` or use a different name.

### 2. `Exec format error`
- **Cause**: Building an image on one architecture (e.g., Apple M1/M2) and running it on another (e.g., Linux x86).
- **Fix**: Use `--platform linux/amd64` during build.

### 3. `Permission denied` (when writing to volumes)
- **Cause**: UID/GID mismatch between host and container.
- **Fix**: Adjust permissions on the host folder or use `chown` inside the Dockerfile.

## Network Troubleshooting

```bash
# List networks
docker network ls

# Inspect a network
docker network inspect <network_name>
```
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
