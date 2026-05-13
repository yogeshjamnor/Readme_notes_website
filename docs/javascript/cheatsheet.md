# JavaScript Cheatsheet

Quick reference for JavaScript syntax and common tasks.

## Types and Equality

- `typeof 42` // "number"
- `typeof "hello"` // "string"
- `typeof true` // "boolean"
- `typeof undefined` // "undefined"
- `typeof null` // "object" (Legacy JS bug)
- `typeof {}` // "object"
- `typeof []` // "object"

**Equality:** Always use `===` (strict) instead of `==` (loose).

## String Methods

```javascript
const str = "Hello World";
str.length;          // 11
str.toUpperCase();   // "HELLO WORLD"
str.trim();          // Remove whitespace
str.includes("lo");  // true
str.split(" ");      // ["Hello", "World"]
```
## Object Methods

```javascript
const obj = { a: 1, b: 2 };
Object.keys(obj);   // ["a", "b"]
Object.values(obj); // [1, 2]
Object.entries(obj);// [["a", 1], ["b", 2]]
```
## JSON Handling

```javascript
const jsonStr = '{"id": 1}';
const obj = JSON.parse(jsonStr);
const str = JSON.stringify(obj);
```
## Useful Browser APIs

- `localStorage.setItem('key', 'value')`
- `localStorage.getItem('key')`
- `setTimeout(() => {}, 1000)`
- `setInterval(() => {}, 1000)`

## Debugging Tips

- `console.log()`: Basic logging.
- `console.table()`: Log arrays/objects as a table.
- `console.error()`: Log errors with stack trace.
- `debugger;`: Set a breakpoint in the code.


## Code Examples

### Common patterns
```javascript
// Deep clone (modern runtimes)
const clone = structuredClone({ a: 1, b: [2, 3] });

// Create a random id (browser + node)
const id = crypto.randomUUID();
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
