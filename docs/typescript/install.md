# Installing TypeScript

Guide to adding TypeScript to your projects in 2026.

## Global Installation (Optional)

```bash
npm install -g typescript
```
## Project Installation (Recommended)

```bash
# Install as dev dependency
npm install -D typescript

# Install common types
npm install -D @types/node
```
## Verifying Installation

```bash
npx tsc --version
```
## Package Manager Options

| Manager | Command |
| :--- | :--- |
| **npm** | `npm install -D typescript` |
| **yarn** | `yarn add -D typescript` |
| **pnpm** | `pnpm add -D typescript` |

## IDE Support

TypeScript is built into **VS Code**. For other editors, you may need a plugin:
- **Sublime Text**: TypeScript plugin.
- **Vim/Neovim**: `coc-tsserver` or `nvim-lspconfig`.
- **JetBrains**: Built-in support.

> [!TIP]
> Use `ts-node` or `tsx` to run TypeScript files directly without a manual compilation step during development.


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