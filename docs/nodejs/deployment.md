# Node.js Deployment Guide

Best practices for deploying Node.js applications to production.

## Environment Preparation

- **NODE_ENV**: Always set to `production`.
- **Port**: Usually set via environment variable (e.g., `process.env.PORT || 3000`).
- **Memory Limits**: Monitor memory usage; Node default heap size may need adjustment.

## Deployment Options

### 1. Platform as a Service (PaaS)
- **Render / Railway / Fly.io**: Connect GitHub repo, specify build command (`npm install`) and start command (`npm start`).

### 2. VPS (DigitalOcean / AWS / GCP)
- Use **Nginx** as a reverse proxy.
- Use **PM2** to manage the Node process.

```bash
# Nginx config snippet
location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
}
```
### 3. Docker
```dockerfile
FROM node:20-slim
WORKDIR /app
COPY package*.json ./
RUN npm install --production
COPY . .
EXPOSE 3000
CMD ["node", "src/index.js"]
```
## Production Checklist

1.  [ ] **Clustering**: Use `cluster` module or PM2 to utilize multiple CPU cores.
2.  [ ] **Logging**: Set up external logging (Datadog, New Relic).
3.  [ ] **Security**: Use `helmet` for HTTP header security.
4.  [ ] **Rate Limiting**: Implement rate limiting for API protection.


## Code Examples

### `fetch` + timeout (Node 18+)
```javascript
const controller = new AbortController();
const timeout = setTimeout(() => controller.abort(), 5000);

try {
  const res = await fetch("https://example.com", { signal: controller.signal });
  console.log(await res.text());
} finally {
  clearTimeout(timeout);
}
```
### Read file as JSON
```javascript
import { readFile } from "node:fs/promises";

const data = JSON.parse(await readFile("config.json", "utf8"));
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
