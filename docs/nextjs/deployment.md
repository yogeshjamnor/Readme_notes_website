# Next.js Deployment

Deploying Next.js applications to production.

## Vercel (Recommended)

Next.js is built by Vercel and offers the best deployment experience.

1.  Connect your GitHub repository.
2.  Vercel automatically detects Next.js.
3.  Configure environment variables in the dashboard.
4.  Push to `main` for automatic deployment.

## Self-Hosting (Node.js)

You can host Next.js on any VPS (DigitalOcean, AWS, etc.).

1.  **Build**: `npm run build`
2.  **Start**: `npm run start` (or use PM2)

```bash
# PM2 Example
pm2 start npm --name "next-app" -- start
```

## Docker Deployment

Example `Dockerfile` for a Next.js application:

```dockerfile
FROM node:20-alpine AS base

# Install dependencies
FROM base AS deps
WORKDIR /app
COPY package.json pnpm-lock.yaml* ./
RUN npm install -g pnpm && pnpm i --frozen-lockfile

# Rebuild the source code
FROM base AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
RUN npm run build

# Production image
FROM base AS runner
WORKDIR /app
ENV NODE_ENV production
COPY --from=builder /app/public ./public
COPY --from=builder /app/.next ./.next
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./package.json

EXPOSE 3000
CMD ["npm", "start"]
```

## Static Export (SSG)

If your app doesn't require server-side features:
```javascript
// next.config.js
/** @type {import('next').NextConfig} */
const nextConfig = {
  output: 'export',
}
```
This generates a `out/` folder that can be hosted anywhere.


## Code Examples

### Environment variables
```bash
# .env.local
NEXT_PUBLIC_API_BASE=https://api.example.com
```

```javascript
// Use NEXT_PUBLIC_* only in the browser.
console.log(process.env.NEXT_PUBLIC_API_BASE);
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
