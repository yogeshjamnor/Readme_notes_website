# Go Cheatsheet

Quick reference for Go syntax used in web development.

## Basics

```go
package main

import \"fmt\"

func main() {
  fmt.Println(\"hello\")
}
```
## Functions

```go
func add(a int, b int) int {
  return a + b
}
```
## Structs

```go
type User struct {
  ID    string
  Email string
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
