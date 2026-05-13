# Node.js Project Setup

Setting up a backend project with Node.js and modern patterns.

## Initializing a Project

```bash
# Initialize npm
npm init -y

# Initialize with TypeScript (Recommended)
npm init -y
npm install -D typescript ts-node @types/node
npx tsc --init
```
## Recommended Folder Structure

```text
root/
├── src/
│   ├── config/       # Configuration (db, env)
│   ├── controllers/  # Request handlers
│   ├── middleware/   # Custom middlewares
│   ├── models/       # DB Schemas/Types
│   ├── routes/       # Route definitions
│   ├── services/     # Business logic
│   ├── utils/        # Helper functions
│   └── index.ts      # App entry point
├── tests/            # Test files
├── .env              # Environment variables
├── .gitignore        # Ignored files
├── package.json      # Dependencies and scripts
└── tsconfig.json     # TS configuration
```
## Environment Variable Setup

Use the `dotenv` package (or native Node.js support for `.env` in newer versions).

```env
PORT=3000
DATABASE_URL=mongodb://localhost:27017/myapp
NODE_ENV=development
JWT_SECRET=your_super_secret_key
```
## Loading Env Variables (Native Node 20.6+)

```bash
node --env-file=.env src/index.ts
```
## Best Practices

1.  **Use ESM**: Use `"type": "module"` in `package.json`.
2.  **Validation**: Use `zod` or `joi` for input validation.
3.  **Error Handling**: Centralized error handling middleware.
4.  **Logging**: Use `winston` or `pino` instead of `console.log` in production.


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
