# Go Project Setup

Minimal setup for a Go HTTP API.

## Minimal HTTP server

```go
package main

import (
  \"net/http\"
)

func main() {
  http.HandleFunc(\"/health\", func(w http.ResponseWriter, r *http.Request) {
    w.Write([]byte(\"ok\"))
  })
  http.ListenAndServe(\":3000\", nil)
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
