# Installing Docker

Guide to installing Docker Engine and Docker Desktop in 2026.

## 1. Docker Desktop (Windows & macOS)

The easiest way to get started with Docker on a workstation.

1.  Download from [docker.com](https://www.docker.com/products/docker-desktop/).
2.  Install and follow the wizard.
3.  Ensure "Use the WSL 2 based engine" is checked on Windows.

## 2. Docker Engine (Linux - Ubuntu)

```bash
# Update and install dependencies
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg

# Add Docker's official GPG key
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
## Verifying Installation

```bash
docker --version
docker compose version
docker run hello-world
```
## System Requirements

| OS | Requirement |
| :--- | :--- |
| **Linux** | 64-bit Kernel version 3.10+ |
| **Windows** | WSL 2 enabled |
| **macOS** | macOS 11+ |

> [!TIP]
> Add your user to the `docker` group on Linux to run commands without `sudo`: `sudo usermod -aG docker $USER`.


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