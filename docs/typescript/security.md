# TypeScript Security Considerations

Using TypeScript features to improve application security.

## 1. Type Safety as a Security Feature
- [ ] **Avoid `any`**: The `any` type bypasses type checking and can hide potential bugs or vulnerabilities. Use `unknown` for data from untrusted sources.
- [ ] **Strict Mode**: Always keep `"strict": true` enabled to catch null/undefined issues that could lead to crashes (DoS).

## 2. Runtime Validation
- [ ] **Type Casting vs Validation**: Remember that TypeScript types disappear at runtime. Always validate external data (API responses, user input) using libraries like **Zod** or **TypeBox**.
```typescript
import { z } from 'zod';

const UserSchema = z.object({
  id: z.number(),
  email: z.string().email(),
});

// Runtime check
const result = UserSchema.safeParse(apiData);
```
## 3. Dependency Security
- [ ] **@types packages**: Ensure you install `@types` from trusted sources.
- [ ] **npm audit**: Scan for vulnerabilities in your development tools and libraries.

## 4. Secure Coding Patterns
- [ ] **Readonly Types**: Use `Readonly<T>` to prevent accidental modification of configuration or sensitive data.
- [ ] **Branded Types**: Use branded types to distinguish between different types of strings (e.g., `UserId` vs `ProductId`) to prevent logic errors.

## 5. Deployment Security
- [ ] **Remove Comments**: Ensure comments and source maps are handled correctly in production to avoid leaking internal logic (unless source maps are needed for error tracking).

> [!TIP]
> Use TypeScript's **Discriminated Unions** to handle API responses safely, ensuring you handle error states before accessing data.


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
## Extra security notes (copy‑ready)

### Dependency scanning
- Keep dependencies updated
- Use the ecosystem scanner (`npm audit`, `pip-audit`, etc.)

### Secrets hygiene
- Do not commit `.env` / private keys
- Rotate leaked keys immediately
