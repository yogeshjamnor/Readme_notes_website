# TypeScript CLI Commands

Commands for compiling and managing TypeScript code.

## Compilation

```bash
# Compile all files based on tsconfig.json
npx tsc

# Compile in watch mode
npx tsc --watch

# Compile a specific file
npx tsc file.ts
```
## Running & Testing

```bash
# Run with tsx (Development)
npx tsx src/index.ts

# Type checking only (no output)
npx tsc --noEmit

# Run tests with Vitest (TS native support)
npx vitest
```
## Maintenance

```bash
# Find and fix formatting issues (with Prettier)
npx prettier --write .

# Find unused dependencies/types (with depcheck or similar)
npx depcheck
```
## Useful CLI Flags

| Flag | Description |
| :--- | :--- |
| `--project <path>` | Specify a configuration file |
| `--showConfig` | Print the effective configuration |
| `--listEmittedFiles` | List files that were output during build |
| `--incremental` | Speed up builds by reusing information from previous runs |

## Useful CLI Shortcuts

- `tsc -p .`: Compile the project in the current directory.
- `tsc --init`: Quick initialization.


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
