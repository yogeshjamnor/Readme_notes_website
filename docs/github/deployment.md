# GitHub Deployment

GitHub typically participates in deployment via CI/CD pipelines.

## Common patterns

- Build/test on PRs
- Deploy preview environments on PRs (optional)
- Deploy to staging/prod on merge/tag

## Release tags

```bash
git tag v1.2.3
```
```bash
git push origin v1.2.3
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
