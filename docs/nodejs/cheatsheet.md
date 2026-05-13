# Node.js Cheatsheet

Quick reference for common Node.js APIs and patterns.

## File System (fs/promises)

```javascript
import fs from 'fs/promises';

// Write file
await fs.writeFile('test.txt', 'Hello World');

// Read file
const data = await fs.readFile('test.txt', 'utf8');

// Check if exists
try {
  await fs.access('test.txt');
} catch {
  // Not exists
}
```
## HTTP Module (Native)

```javascript
import http from 'http';

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello World');
});

server.listen(3000);
```
## Process Object

- `process.env.VAR_NAME`: Environment variables.
- `process.argv`: CLI arguments.
- `process.cwd()`: Current working directory.
- `process.exit(0)`: Exit process with success.

## Streams

```javascript
import fs from 'fs';

const readable = fs.createReadStream('large.txt');
const writable = fs.createWriteStream('copy.txt');

readable.pipe(writable);
```
## Useful Global Variables

- `__dirname`: Current directory (CommonJS only).
- `__filename`: Current file (CommonJS only).
- `import.meta.url`: Current module URL (ESM).
- `console.table()`: Print objects in a table format.


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
