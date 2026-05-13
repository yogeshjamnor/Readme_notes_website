# PHP Commands

Common PHP + Composer commands for web projects.

## PHP runtime

```bash
php -v
php -m
php -i | rg \"Loaded Configuration\"
```
## Composer

```bash
composer --version
composer install
composer update
composer dump-autoload
composer audit
```
## Local server (dev only)

```bash
php -S localhost:8000 -t public
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
