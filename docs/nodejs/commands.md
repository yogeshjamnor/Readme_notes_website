# Node.js CLI Commands

Essential commands for managing and running Node.js applications.

## Development Server

Use `nodemon` or the native `--watch` flag for auto-restart.

```bash
# Using nodemon
npx nodemon src/index.js

# Using native Node watch (Node 18+)
node --watch src/index.js
```
## Package Manager Commands

| Action | npm | yarn | pnpm |
| :--- | :--- | :--- | :--- |
| **Install all** | `npm install` | `yarn` | `pnpm install` |
| **Add package** | `npm i <pkg>` | `yarn add <pkg>` | `pnpm add <pkg>` |
| **Add dev dev** | `npm i -D <pkg>` | `yarn add -D <pkg>`| `pnpm add -D <pkg>`|
| **Remove package**| `npm uninstall <pkg>`| `yarn remove <pkg>` | `pnpm remove <pkg>`|
| **Run script** | `npm run <name>` | `yarn <name>` | `pnpm <name>` |

## Production Commands

```bash
# Standard start
npm start

# Using PM2 (Process Manager)
npm install -g pm2
pm2 start src/index.js --name "my-app"
pm2 list
pm2 stop all
pm2 delete all
```
## Auditing and Security

```bash
# Check for vulnerabilities
npm audit

# Fix vulnerabilities automatically
npm audit fix
```
## Useful CLI Shortcuts

- `node -e "console.log(1+1)"`: Evaluate JS in terminal.
- `node -p "os.platform()"`: Evaluate and print.
- `npm link`: Symlink a package for local development.


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
