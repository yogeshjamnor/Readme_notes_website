# Docker Deployment

Strategies for deploying Docker containers to production.

## Container Registries

Before deploying, you must push your image to a registry.

1.  **Docker Hub**: `docker push username/repo:tag`
2.  **GitHub Container Registry (GHCR)**: `docker push ghcr.io/username/repo:tag`
3.  **AWS ECR / Google Artifact Registry**: Cloud-specific registries.

## Deployment Options

| Option | Scale | Use Case |
| :--- | :--- | :--- |
| **Single VPS** | Small | Docker Compose with Nginx |
| **PaaS (Railway/Render)** | Medium | Automated Docker builds from GitHub |
| **AWS ECS / Fargate** | Large | Managed container orchestration |
| **Kubernetes (K8s)** | Enterprise | Complex, multi-service orchestration |

## CI/CD Pipeline (GitHub Actions)

```yaml
steps:
  - uses: actions/checkout@v4
  - name: Login to Docker Hub
    uses: docker/login-action@v3
    with:
      username: ${{ secrets.DOCKERHUB_USERNAME }}
      password: ${{ secrets.DOCKERHUB_TOKEN }}
  - name: Build and push
    uses: docker/build-push-action@v5
    with:
      push: true
      tags: user/app:latest
```
## Production Hardening

- [ ] **Limit Resources**: Use `--memory` and `--cpus` to prevent a single container from hogging system resources.
- [ ] **Read-Only Root FS**: Use `--read-only` if your app doesn't need to write to the local filesystem.
- [ ] **Health Checks**: Use the `HEALTHCHECK` instruction in your Dockerfile.
- [ ] **Secrets Management**: Never use `ENV` for secrets; use Docker Secrets or cloud provider vault.


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
