# Docker Security Checklist

Guidelines for building and running secure containers.

## 1. Image Security
- [ ] **Base Image**: Use official, minimal base images (e.g., `alpine`, `slim`).
- [ ] **Scan Images**: Use `docker scout` or `trivy` to find vulnerabilities in your images.
- [ ] **Trusted Registries**: Only pull images from trusted sources.

## 2. Dockerfile Hardening
- [ ] **Non-Root User**: Always run your application as a non-root user.
  ```dockerfile
  RUN adduser -D myuser
  USER myuser
  ```
- [ ] **Multi-Stage Builds**: Keep production images clean of build tools and source code.
- [ ] **Secret Management**: Never use `ENV` for secrets. Use Docker Secrets or mount secret files.

## 3. Runtime Security
- [ ] **Limit Resources**: Use `--memory` and `--cpus` to prevent DoS from a single container.
- [ ] **Read-Only Filesystem**: Run containers with `--read-only` where possible.
- [ ] **Capabilities**: Drop unnecessary Linux capabilities.
  ```bash
  docker run --cap-drop=ALL --cap-add=NET_BIND_SERVICE ...
  ```

## 4. Network Security
- [ ] **Internal Networks**: Use Docker bridge networks to isolate containers.
- [ ] **Port Exposure**: Only expose necessary ports (`EXPOSE` in Dockerfile and `-p` at runtime).

## 5. Security Tools
| Tool | Purpose |
| :--- | :--- |
| **Docker Scout** | Built-in image vulnerability scanning |
| **Trivy** | Comprehensive security scanner for containers |
| **Hadolint** | Linter for Dockerfiles (catches security smells) |

## 6. Audit & Logging
- [ ] **Container Logs**: Centralize logs to monitor for suspicious activity.
- [ ] **Daemon Security**: Ensure the Docker daemon is configured securely (`/etc/docker/daemon.json`).

> [!CAUTION]
> Avoid using the `--privileged` flag unless absolutely necessary, as it gives the container full access to the host system.


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
## Extra security notes (copy‑ready)

### Run as non‑root
```dockerfile
RUN addgroup -S app && adduser -S app -G app
USER app
```
### Pin base images + scan
```bash
docker pull node:20-alpine
# Prefer digest pinning in production:
# FROM node:20-alpine@sha256:...
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
