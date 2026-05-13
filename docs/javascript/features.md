# Modern JavaScript Features

A guide to ES6+ features and essential array methods in 2026.

## 1. ES6+ Core Features

### Let and Const
```javascript
const pi = 3.14; // Constant
let counter = 0; // Block-scoped variable
```
### Arrow Functions
```javascript
const add = (a, b) => a + b;
```
### Template Literals
```javascript
const name = "World";
console.log(`Hello, ${name}!`);
```
### Destructuring
```javascript
const user = { id: 1, name: "Alice" };
const { id, name } = user;

const colors = ["red", "green", "blue"];
const [first, second] = colors;
```
### Spread & Rest Operators
```javascript
// Spread
const newArr = [...colors, "yellow"];
const newUser = { ...user, age: 25 };

// Rest
const sum = (...args) => args.reduce((a, b) => a + b, 0);
```
## 2. Essential Array Methods

### `.map()`
Creates a new array by performing a function on each element.
```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2); // [2, 4, 6]
```
### `.filter()`
Creates a new array with elements that pass a test.
```javascript
const evens = numbers.filter(n => n % 2 === 0); // [2]
```
### `.reduce()`
Reduces the array to a single value.
```javascript
const total = numbers.reduce((acc, curr) => acc + curr, 0); // 6
```
### `.sort()`
Sorts the elements (mutates the original array).
```javascript
const fruits = ["banana", "apple", "cherry"];
fruits.sort(); // ["apple", "banana", "cherry"]

// Numerical sort
const scores = [40, 100, 1, 5, 25];
scores.sort((a, b) => a - b); // [1, 5, 25, 40, 100]
```
### `.splice()`
Adds/removes elements (mutates the original array).
```javascript
const months = ['Jan', 'March', 'April'];
months.splice(1, 0, 'Feb'); // Inserts at index 1
// months: ['Jan', 'Feb', 'March', 'April']
```
## 3. Async/Await
```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error(error);
  }
}
```
## 4. Newer Syntax (ES2020+)

### Optional Chaining (`?.`) and Nullish Coalescing (`??`)
```javascript
const user = { profile: { name: "Asha" } };

// Optional chaining
const city = user.address?.city; // undefined (no crash)

// Nullish coalescing (only falls back for null/undefined)
const displayName = user.profile?.name ?? "Anonymous";
```
### Logical Assignment Operators
```javascript
let token = "";

token ||= "generated-token"; // sets only if token is falsy
```
### Promise Helpers (`allSettled`)
```javascript
const results = await Promise.allSettled([
  fetch("/a").then(r => r.json()),
  fetch("/b").then(r => r.json()),
]);

const failures = results.filter(r => r.status === "rejected");
```
### Copy‑ready example: safe JSON parse
```javascript
export function safeJsonParse(text) {
  try {
    return { ok: true, value: JSON.parse(text) };
  } catch (err) {
    return { ok: false, error: err };
  }
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
