# TypeScript Setup

Initializing and configuring TypeScript projects.

## Initialization

```bash
npx tsc --init
```
This creates a `tsconfig.json` file in your root directory.

## Recommended `tsconfig.json` (Strict)

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist",
    "rootDir": "./src",
    "resolveJsonModule": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "**/*.spec.ts"]
}
```
## Running TS Files Directly

```bash
# Using tsx (Modern & Fast)
npx tsx src/index.ts

# Using ts-node
npx ts-node src/index.ts
```
## Best Practices

1.  **Strict Mode**: Always keep `"strict": true` enabled.
2.  **Explicit Types**: While inference is good, explicit types for function parameters and return values improve readability.
3.  **Avoid `any`**: Use `unknown` if you're not sure, or better yet, define an interface.
4.  **Utility Types**: Familiarize yourself with `Partial`, `Readonly`, `Pick`, and `Omit`.

> [!IMPORTANT]
> Ensure `"module": "NodeNext"` if you are building for modern Node.js environments using ESM.


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
