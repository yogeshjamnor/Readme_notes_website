# Next.js CLI Commands

Common commands for developing and building Next.js apps.

## Development

```bash
# Start development server
npm run dev

# Start development server on specific port
npm run dev -- -p 4000
```

## Build & Production

```bash
# Create production build
npm run build

# Start production server (locally)
npm run start
```

## Maintenance & Linting

```bash
# Run ESLint
npm run lint

# Check for TS errors
npx tsc --noEmit
```

## CLI Tools (npx)

```bash
# Generate components or routes (if using a generator)
npx shadcn@latest add button

# Analyze bundle size
npx next-bundle-analyzer
```

## Useful CLI Shortcuts

- `rs`: Restart the development server.
- `Ctrl + C`: Stop the server.
- `next telemetry disable`: Opt-out of anonymous usage data collection.

| Script | Purpose |
| :--- | :--- |
| `dev` | Development mode with Hot Module Replacement |
| `build` | Optimizes the application for production |
| `start` | Runs the optimized build |
| `lint` | Runs static code analysis |


## Code Examples

### Environment variables
```bash
# .env.local
NEXT_PUBLIC_API_BASE=https://api.example.com
```

```javascript
// Use NEXT_PUBLIC_* only in the browser.
console.log(process.env.NEXT_PUBLIC_API_BASE);
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
