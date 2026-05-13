# GitHub Debugging (CI + PR checks)

How to quickly debug common GitHub and CI issues.

## Check what failed

- Open the failing check → read logs from top to bottom once.
- Re-run only the failed job if possible.

## Common local mirrors

```bash
# run unit tests
```
```bash
npm test
```
```bash
# lint
```
```bash
npm run lint
```

## “It works locally” checklist

- Same Node version as CI
- Fresh install (`rm -rf node_modules && npm ci`)
- No uncommitted changes



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
