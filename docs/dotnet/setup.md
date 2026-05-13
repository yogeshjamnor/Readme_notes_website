# .NET Web Setup (Minimal API)

Minimal API example structure.

## Minimal API

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet(\"/health\", () => Results.Ok(\"ok\"));

app.Run();
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
