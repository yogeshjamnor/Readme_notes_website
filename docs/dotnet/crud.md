# .NET CRUD (Minimal API style)

Basic CRUD endpoints outline (pattern).

```csharp
app.MapPost("/users", async (CreateUserDto dto) => Results.Created());
app.MapGet("/users/{id}", async (string id) => Results.Ok());
app.MapPut("/users/{id}", async (string id, UpdateUserDto dto) => Results.NoContent());
app.MapDelete("/users/{id}", async (string id) => Results.NoContent());
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
