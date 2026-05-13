# Linux Security Hardening Checklist

Essential steps to secure a Linux system.

## 1. Access Control
- [ ] **SSH**: Disable root login and use SSH keys instead of passwords.
  ```bash
# Edit /etc/ssh/sshd_config
```bash
```
PermitRootLogin no
```bash
```
PasswordAuthentication no
```bash
- [ ] **Sudo**: Limit `sudo` access to specific users and use `visudo` for configuration.
- [ ] **MFA**: Consider adding 2FA (e.g., Google Authenticator) for SSH.

## 2. Network Security
- [ ] **Firewall**: Enable and configure `ufw` or `firewalld`.
  ```bash
sudo ufw default deny incoming
```
```bash
sudo ufw allow ssh
```
```bash
sudo ufw allow http
```
```bash
sudo ufw enable
```
- [ ] **Fail2Ban**: Install and configure Fail2Ban to block brute-force attempts.
- [ ] **Unused Ports**: Regularly check for listening ports with `netstat -tuln` and close unnecessary ones.

## 3. System Updates
- [ ] **Automated Updates**: Use `unattended-upgrades` (Ubuntu/Debian) to install security patches automatically.
- [ ] **Kernel**: Keep the kernel updated.

## 4. File System & Monitoring
- [ ] **File Permissions**: Regularly check for world-writable files and directories.
- [ ] **Auditing**: Use `auditd` to track changes to sensitive files like `/etc/passwd`.
- [ ] **Rootkits**: Scan for rootkits using `rkhunter` or `chkrootkit`.

## 5. Security Tools
| Tool | Purpose |
| :--- | :--- |
| **UFW** | Uncomplicated Firewall |
| **Fail2Ban** | Brute-force protection |
| **Lynis** | Security auditing tool |
| **ClamAV** | Open-source antivirus |

## 6. Practical Hardening Example
```bash
# Set secure permissions for sensitive files
```
```bash
sudo chmod 600 /etc/shadow
```
```bash
sudo chmod 600 /etc/gshadow
```
> [!CAUTION]
> Always test firewall rules and SSH configurations in a separate session before closing your current connection to avoid being locked out.


## Code Examples

### Find large files
```bash
find . -type f -size +100M -print
```
### Grep recursively (ripgrep)
```bash
rg "TODO|FIXME" -n .
```
## Extra security notes (copy‑ready)

### Check listening ports
```bash
ss -tulpn
```
### Quick file permission audit
```bash
find . -type f -perm -o+w -print
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
