# .NET Deployment

High-level deployment steps for .NET web services.

## Publish

```bash
dotnet publish -c Release -o out
```

## Checklist

- Set `ASPNETCORE_URLS` / reverse proxy config
- Store secrets in a secret manager (not in repo)
- Run behind a process manager / container



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
