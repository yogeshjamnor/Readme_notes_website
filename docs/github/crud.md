# GitHub CRUD (Issues/PRs)

“CRUD” here means your daily actions: create/update/close issues and PRs.

## Create an issue

```bash
gh issue create --title "Bug: login fails" --body "Steps to reproduce..."
```

## Create a PR

```bash
gh pr create --fill
```

## Update a PR (push new commits)

```bash
git add -A
```
```bash
git commit -m "fix: handle edge case"
```
```bash
git push
```

## Close an issue

```bash
gh issue close 123 --comment "Fixed via #456"
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
