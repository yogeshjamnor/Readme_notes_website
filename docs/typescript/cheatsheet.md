# TypeScript Cheatsheet

Quick reference for TypeScript syntax and utility types.

## Basic Types

```typescript
let isDone: boolean = false;
let lines: number = 42;
let name: string = "Alice";
let list: number[] = [1, 2, 3];
let tuple: [string, number] = ["hello", 10];
```
## Interfaces and Types

```typescript
interface User {
  id: number;
  name: string;
  age?: number; // Optional
}

type ID = string | number; // Union type
```
## Functions

```typescript
function add(x: number, y: number): number {
  return x + y;
}

const multiply = (x: number, y: number): number => x * y;
```
## Utility Types

| Type | Description |
| :--- | :--- |
| `Partial<T>` | All properties in T become optional |
| `Required<T>` | All properties in T become required |
| `Readonly<T>` | All properties in T are read-only |
| `Pick<T, K>` | Select specific properties K from T |
| `Omit<T, K>` | Remove specific properties K from T |
| `Record<K, T>`| Object with keys K and values T |

## Generics

```typescript
function identity<T>(arg: T): T {
  return arg;
}

const output = identity<string>("myString");
```
## Keyof and Typeof

```typescript
const person = { name: "John", age: 30 };
type Person = typeof person;
type PersonKeys = keyof Person; // "name" | "age"
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
