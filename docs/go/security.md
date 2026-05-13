# Go Security

Security practices for Go web services.

## 1. Parameterized queries
- Use placeholders (`?` / `$1`) in SQL instead of string concatenation.

## 2. Timeouts and cancellation

```go
ctx, cancel := context.WithTimeout(r.Context(), 2*time.Second)
defer cancel()
```
## 3. Input validation
- Validate JSON payloads and enforce length limits.



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
