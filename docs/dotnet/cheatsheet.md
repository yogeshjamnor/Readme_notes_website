# C#/.NET Cheatsheet

Quick reference for C# (modern) used in web development.

## Basics

```csharp
var name = \"World\";
int count = 3;
bool ok = true;
```

## Records / DTOs

```csharp
public record UserDto(string Id, string Email);
```

## Async/await

```csharp
var text = await httpClient.GetStringAsync(\"https://example.com\");
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
