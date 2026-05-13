# GitHub Commands (CLI + Git)

Common daily commands. Requires `git` and optionally `gh` (GitHub CLI).

## Git basics

```bash
git status
```
```bash
git add -A
```
```bash
git commit -m "feat: add thing"
```
```bash
git push
```

## Branch workflow

```bash
git checkout -b feature/my-task
```
```bash
git push -u origin feature/my-task
```

## Rebase (keep history clean)

```bash
git fetch origin
```
```bash
git rebase origin/main
```

## GitHub CLI (`gh`)

```bash
gh auth status
```
```bash
gh repo view --web
```
```bash
gh pr create --fill
```
```bash
gh pr status
```
```bash
gh pr checkout 123
```
```bash
gh issue create
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
