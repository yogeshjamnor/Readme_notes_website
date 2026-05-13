# PHP Project Setup

Simple structure that works for many PHP web projects.

## Minimal layout

```text
project/
  public/
    index.php
  src/
  vendor/
  composer.json
```
## Autoloading (Composer)

```json
{
  "autoload": {
    "psr-4": { "App\\\\": "src/" }
  }
}
```
```bash
composer dump-autoload
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
