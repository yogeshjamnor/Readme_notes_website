# Installing Node.js

Guide to installing Node.js and its ecosystem in 2026.

## Using NVM (Recommended)

Node Version Manager (NVM) allows you to manage multiple Node versions.

```bash
# Install nvm (sh/bash)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Install specific Node version
nvm install 20 # Latest LTS

# Use specific version
nvm use 20

# Set default version
nvm alias default 20
```
## Direct Installation

- **Windows**: Download the `.msi` from [nodejs.org](https://nodejs.org).
- **macOS**: `brew install node`
- **Linux (Ubuntu/Debian)**:
  ```bash
  curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
  sudo apt-get install -y nodejs
  ```

## Verifying Installation

```bash
node -v
npm -v
```
## Package Managers

| Manager | Install Command | Use Case |
| :--- | :--- | :--- |
| **npm** | Bundled with Node | Standard/Default |
| **yarn** | `npm install -g yarn` | Fast/Predictable |
| **pnpm** | `npm install -g pnpm` | Disk efficient/Strict |

> [!TIP]
> Use `corepack` to manage package managers without global installs: `corepack enable`.


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