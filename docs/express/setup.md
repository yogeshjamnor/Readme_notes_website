# Express.js Project Setup

Setting up a robust Express application server.

## Basic Server Boilerplate (ESM)

```javascript
import express from 'express';
import cors from 'cors';
import dotenv from 'dotenv';
import helmet from 'helmet';

dotenv.config();

const app = express();
const PORT = process.env.PORT || 3000;

// Middlewares
app.use(helmet());
app.use(cors());
app.use(express.json());

// Basic Route
app.get('/', (req, res) => {
  res.json({ message: 'API is running' });
});

// Start Server
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```
## Recommended Folder Structure

```text
src/
├── app.js            # Express app configuration
├── server.js         # Entry point (listens on port)
├── routes/           # API routes
├── controllers/      # Route logic
├── models/           # Data models
├── middleware/       # Custom middlewares
└── utils/            # Helper functions
```
## Middleware Best Practices

1.  **Error Handling Middleware**: Place at the end of the middleware stack.
    ```javascript
    app.use((err, req, res, next) => {
      console.error(err.stack);
      res.status(500).send('Something broke!');
    });
    ```
2.  **Async Wrapper**: Use an async wrapper to catch errors in async routes (if not using Express 5).

> [!IMPORTANT]
> Always use `express.json()` to parse JSON request bodies.


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
