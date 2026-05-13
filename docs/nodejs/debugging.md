# Debugging Node.js Applications

Effective ways to debug server-side JavaScript.

## Chrome DevTools Integration

You can debug Node.js using Chrome's debugger.

```bash
node --inspect src/index.js
# Or to break at start
node --inspect-brk src/index.js
```
Then open `chrome://inspect` in your browser.

## VS Code Debugger

1.  Click the "Run and Debug" icon.
2.  Select "Node.js".
3.  Set breakpoints in your code.

## Common Errors and Fixes

### 1. `EADDRINUSE: address already in use :::3000`
- **Cause**: Another process is using port 3000.
- **Fix**: Kill the process or use a different port.
  ```bash
  kill -9 $(lsof -t -i:3000)
  ```

### 2. `ERR_MODULE_NOT_FOUND`
- **Cause**: Missing file extension in ESM imports or file doesn't exist.
- **Fix**: Add `.js` or `.ts` extension to imports.

### 3. `ReferenceError: process is not defined` (in browser)
- **Cause**: Trying to access Node globals in client-side code.
- **Fix**: Check your environment or use a bundler (Vite/Webpack) that shims `process`.

## Profiling

```bash
# Generate CPU profile
node --prof src/index.js

# Process the profile
node --prof-process isolate-0xnnnnnnnnnnnn-v8.log > processed.txt
```
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
