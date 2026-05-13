# Linux Server Deployment

Best practices for deploying applications on a Linux server.

## 1. Using Systemd

Run your application as a background service that auto-restarts on failure.

Create `/etc/systemd/system/myapp.service`:
```ini
[Unit]
Description=My Application
After=network.target

[Service]
User=www-data
WorkingDirectory=/var/www/myapp
ExecStart=/usr/bin/node server.js
Restart=always

[Install]
WantedBy=multi-user.target
```
```bash
sudo systemctl daemon-reload
```
```bash
sudo systemctl enable myapp
```
```bash
sudo systemctl start myapp
```
## 2. Reverse Proxy (Nginx)

Expose your application to the web on port 80/443.

```nginx
server {
    listen 80;
    server_name example.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
    }
}
```
## 3. SSL/TLS (Certbot)

```bash
sudo apt install certbot python3-certbot-nginx
```
```bash
sudo certbot --nginx -d example.com
```
## 4. Automation & Config Management

- **Ansible**: Automate server configuration.
- **Terraform**: Infrastructure as Code.
- **GitHub Actions**: Deploy via SSH or Docker.

## 5. Security Hardening

- [ ] **SSH Config**: Disable root login and password auth (`/etc/ssh/sshd_config`).
- [ ] **Firewall**: Use `ufw` to block all but 80, 443, and your SSH port.
- [ ] **Fail2Ban**: Automatically block IPs with too many failed login attempts.
- [ ] **Automatic Updates**: Use `unattended-upgrades`.


## Code Examples

### Find large files
```bash
find . -type f -size +100M -print
```
### Grep recursively (ripgrep)
```bash
rg "TODO|FIXME" -n .
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
