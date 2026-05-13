# .NET Security

Security practices for ASP.NET Core web apps.

## 1. Secrets
- Use User Secrets (dev) and a secret manager (prod). Never commit secrets.

## 2. Authentication & authorization
- Enforce authorization on the server for protected resources.

## 3. Input validation
- Validate DTOs and enforce size limits.

## Code Examples

### Example: set security headers
```csharp
app.Use(async (ctx, next) =>
{
  ctx.Response.Headers["X-Content-Type-Options"] = "nosniff";
  await next();
});
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
