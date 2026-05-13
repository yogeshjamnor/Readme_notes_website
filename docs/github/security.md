# GitHub Security

Practical security for repos and workflows.

## 1. Protect branches
- Require PR reviews
- Require status checks
- Disallow force-push to `main`

## 2. Secrets
- Use GitHub Actions secrets (never commit `.env`/keys)
- Rotate secrets if leaked

## 3. Dependency scanning
- Enable Dependabot updates
- Use code scanning if available

## Code Examples

### GitHub Actions: use secrets safely
```yaml
env:
  API_TOKEN: ${{ secrets.API_TOKEN }}
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
