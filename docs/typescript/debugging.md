# Debugging TypeScript

Tools and techniques for troubleshooting TypeScript applications.

## Using VS Code Debugger

TypeScript works seamlessly with the built-in VS Code debugger.

1.  Create a `.vscode/launch.json`:
    ```json
    {
      "version": "0.2.0",
      "configurations": [
        {
          "type": "node",
          "request": "launch",
          "name": "Debug TS",
          "runtimeArgs": ["-r", "tsx/register"],
          "args": ["${workspaceFolder}/src/index.ts"]
        }
      ]
    }
    ```
2.  Set breakpoints and start debugging (F5).

## Common Errors

### 1. `Property 'X' does not exist on type 'Y'`
- **Cause**: Trying to access a property that TS doesn't think exists on the object.
- **Fix**: Check your interface/type definition, use optional chaining `?.`, or type assertions `as Y`.

### 2. `Argument of type 'X' is not assignable to parameter of type 'Y'`
- **Cause**: Type mismatch between what is passed and what is expected.
- **Fix**: Align the types or use a union type `X | Y`.

### 3. `Module not found`
- **Cause**: Missing `@types` package or incorrect import path.
- **Fix**: Run `npm install -D @types/<package>` or check your `tsconfig.json` `paths`.

## Logging Types

For complex types, you can use the following trick to inspect them in your IDE:

```typescript
type Inspect<T> = { [K in keyof T]: T[K] } & {};
```
## Useful Tools

- **TS-Error-Translator**: Chrome extension/website to make TS errors readable.
- **Zod**: Runtime type validation that syncs with TS types.
- **TypeScript PlayGround**: Online environment to test TS snippets.


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
