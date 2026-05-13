# Ruby Project Setup

Simple setup options for Ruby web apps.

## Sinatra (minimal)

```bash
bundle init
bundle add sinatra
```
```rb
require \"sinatra\"

get \"/health\" do
  \"ok\"
end
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
