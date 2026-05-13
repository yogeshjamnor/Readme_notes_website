# Debugging Linux Systems

Tools and techniques for troubleshooting system and application issues.

## Viewing System Logs (Journalctl)

```bash
# View all logs
```
```bash
journalctl
```
```bash
# View logs for a specific service
```
```bash
journalctl -u myapp.service -f
```
```bash
# View kernel logs
```
```bash
dmesg -T
```
## Process Debugging

```bash
# Trace system calls of a process
```
```bash
strace -p <pid>
```
```bash
# List open files of a process
```
```bash
lsof -p <pid>
```
```bash
# Show which process is using a port
```
```bash
sudo lsof -i :3000
```
## Network Debugging

```bash
# Check DNS resolution
```
```bash
nslookup google.com
```
```bash
# Trace network path
```
```bash
traceroute google.com
```
```bash
# Dump network traffic
```
```bash
sudo tcpdump -i eth0
```
## Common Issues

### 1. `Permission Denied`
- **Cause**: Trying to execute/read a file without proper permissions or as a non-root user.
- **Fix**: Use `sudo`, `chmod`, or `chown`.

### 2. `No space left on device`
- **Cause**: Disk is full.
- **Fix**: Identify large files with `du -sh * | sort -h` and delete unnecessary data.

### 3. `Connection Refused`
- **Cause**: Service not running or firewall blocking the port.
- **Fix**: `systemctl status <service>` or `ufw status`.

## Recovery Mode

If the system fails to boot, use a Live USB to `chroot` into the system and fix configurations.


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
