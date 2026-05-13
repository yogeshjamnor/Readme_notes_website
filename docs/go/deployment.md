# Go Deployment

Go is commonly deployed as a single compiled binary.

## Build

```bash
go build -o app .
```
## Checklist

- Use `-trimpath` and strip symbols for smaller builds if desired
- Configure env vars outside the binary
- Put behind a reverse proxy (Nginx) if needed



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
