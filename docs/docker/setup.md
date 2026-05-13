# Docker Setup

Configuring Docker for development and production.

## Dockerfile Basics

A `Dockerfile` defines how to build an image for your application.

```dockerfile
# Choose a base image
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Expose the application port
EXPOSE 3000

# Command to run the application
CMD ["npm", "start"]
```
## `.dockerignore`

Always include a `.dockerignore` file to prevent copying unnecessary files (like `node_modules` or `.git`) into the image.

```text
node_modules
npm-debug.log
dist
.git
.env
```
## Docker Compose Setup

Use `docker-compose.yml` to define multi-container applications.

```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=development
    volumes:
      - .:/app
      - /app/node_modules
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: password
```
## Best Practices

1.  **Use Small Base Images**: Prefer `alpine` or `slim` variants.
2.  **Layer Caching**: Copy `package.json` and install dependencies *before* copying the rest of the code.
3.  **Non-Root User**: Run your application as a non-root user for better security.
4.  **Multi-Stage Builds**: Use multi-stage builds to keep production images small.


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
