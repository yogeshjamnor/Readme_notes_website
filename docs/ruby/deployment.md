# Ruby Deployment

High-level deployment checklist for Ruby web apps.

## Common stack

- App server: Puma
- Reverse proxy: Nginx
- Process manager: systemd

## Checklist

- Precompile assets (Rails) if needed
- Set secrets via environment variables/secret manager
- Pin and audit gems



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
