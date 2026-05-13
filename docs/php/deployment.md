# PHP Deployment

High-level deployment checklist for PHP web apps.

## Common stack

- Nginx/Apache
- PHP-FPM
- Process manager / service (systemd)

## Checklist

- Use `composer install --no-dev` in production
- Set correct file permissions (do not allow writable source)
- Configure environment variables outside the repo



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
