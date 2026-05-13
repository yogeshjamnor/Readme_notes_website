# GitHub Setup

Practical setup for day-to-day GitHub use.

## Configure Git identity

```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "you@example.com"
```

## SSH key (recommended)

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```
```bash
cat ~/.ssh/id_ed25519.pub
```

## Typical repo defaults

- Branch protection on `main`
- Required PR reviews
- CI required to pass
- Code owners (`.github/CODEOWNERS`)



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
