# Express.js Deployment

Deploying Express APIs to production.

## Production Optimization

- **Gzip Compression**: Use the `compression` middleware.
  ```javascript
  import compression from 'compression';
  app.use(compression());
  ```
- **Trust Proxy**: If behind Nginx or Load Balancer.
  ```javascript
  app.set('trust proxy', 1);
  ```

## Hosting Options

| Platform | Deployment Type |
| :--- | :--- |
| **AWS Lambda** | Serverless (requires `serverless-http`) |
| **DigitalOcean** | VPS with PM2 & Nginx |
| **Heroku** | PaaS (Git-based) |
| **Railway** | Modern PaaS |

## Docker Compose Example

```yaml
services:
  api:
    build: .
    ports:
      - "3000:3000"
    environment:
      - MONGO_URL=mongodb://db:27017/myapp
    depends_on:
      - db
  db:
    image: mongo:latest
    ports:
      - "27017:27017"
```
## Security Checklist

1.  [ ] **Helmet**: Use `app.use(helmet())`.
2.  [ ] **Rate Limiting**: Use `express-rate-limit`.
3.  [ ] **CORS**: Restrict origins to allowed domains.
4.  [ ] **Input Sanitization**: Use `express-validator`.


## Code Examples

### Centralized error handler
```javascript
app.use((err, req, res, next) => {
  const status = err.statusCode ?? 500;
  res.status(status).json({
    message: err.message ?? "Internal Server Error",
  });
});
```
### Async route wrapper
```javascript
export const wrap = (fn) => (req, res, next) =>
  Promise.resolve(fn(req, res, next)).catch(next);
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
