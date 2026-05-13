# TypeScript Deployment

Best practices for deploying TypeScript applications.

## Compilation for Production

Never run `ts-node` or `tsx` in production. Always compile to JavaScript first.

1.  **Build step**:
    ```bash
    npm run build # usually runs 'tsc'
    ```
2.  **Run step**:
    ```bash
    node dist/index.js
    ```

## CI/CD Pipeline Integration

Ensure your CI/CD pipeline includes a type-checking step to prevent bugs from reaching production.

```yaml
# GitHub Actions example snippet
steps:
  - uses: actions/checkout@v4
  - name: Install dependencies
    run: npm install
  - name: Type check
    run: npx tsc --noEmit
  - name: Build
    run: npm run build
```
## Source Maps

Enable source maps in `tsconfig.json` for easier debugging of production crashes.

```json
{
  "compilerOptions": {
    "sourceMap": true
  }
}
```
## Handling Node Modules

In 2026, many libraries are ESM-first. Ensure your deployment environment and `tsconfig.json` are aligned with ESM requirements (`"type": "module"` in `package.json`).

## Docker Deployment

```dockerfile
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npx tsc

FROM node:20-alpine
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/package*.json ./
RUN npm install --production
CMD ["node", "dist/index.js"]
```
## Code Examples

### Utility types
```ts
type User = { id: string; name: string; email?: string };

type UserRequired = Required<User>;
type UserPublic = Omit<User, "email">;
```
### Safer `unknown` parsing
```ts
function isString(value: unknown): value is string {
  return typeof value === "string";
}

const input: unknown = "hello";
if (isString(input)) {
  input.toUpperCase();
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
