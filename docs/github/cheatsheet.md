# GitHub Cheatsheet

Daily-use GitHub features and shortcuts for web developers.

## Issues & PRs

- Use Issues for tasks/bugs and PRs for changes.
- Prefer small PRs with clear descriptions and screenshots when UI changes.
- Link PRs to Issues (e.g., “Fixes #123”) to auto-close on merge.

## Markdown (PR/Issue description)

```md
## What
- Summary of change

## Why
- Reason / context

## How to test
1. Steps

## Screenshots
- Before/After (if UI)
```

## CODEOWNERS (review routing)

```text
# .github/CODEOWNERS
*       @your-org/platform
/api/   @your-org/backend
/web/   @your-org/frontend
```

## Code Examples

### PR checklist template
```md
- [ ] Tests added/updated
- [ ] Lint/format passes
- [ ] Docs updated (if needed)
- [ ] Screenshots for UI changes
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
