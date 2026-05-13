# React Deployment Guide

Deploying React applications to production environments.

## Static Hosting (Vercel, Netlify, GitHub Pages)

Most React apps are Single Page Applications (SPAs) and can be hosted as static files.

1.  **Build the project**:
    ```bash
    npm run build
    ```
2.  **Upload the `dist/` folder**:
    The build output is located in the `dist/` directory (for Vite) or `build/` (for CRA).

## Production Best Practices

- **Enable Compression**: Use Gzip or Brotli on the server.
- **Cache Control**: Set long cache headers for assets (JS, CSS, Images).
- **Environment Variables**: Ensure production API keys are set in the hosting provider's dashboard.
- **Error Tracking**: Integrate Sentry or LogRocket for production error monitoring.

## Docker Deployment

Example `Dockerfile` for a React app using Nginx:

```dockerfile
# Build Stage
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Production Stage
FROM nginx:stable-alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
## SPA Routing Fix (Nginx)

When using React Router, ensure all requests redirect to `index.html`.

```nginx
location / {
  try_files $uri $uri/ /index.html;
}
```
## Code Examples

### `useMemo` for derived values
```jsx
import { useMemo } from "react";

function Total({ items }) {
  const total = useMemo(
    () => items.reduce((sum, item) => sum + item.price, 0),
    [items]
  );

  return <div>Total: {total}</div>;
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
