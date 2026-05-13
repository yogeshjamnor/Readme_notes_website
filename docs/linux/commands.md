# Linux CLI Commands

Essential commands for navigating and managing a Linux system.

## File & Directory Operations

| Command | Description |
| :--- | :--- |
| `ls -lah` | List files with details and hidden files |
| `cd <dir>` | Change directory |
| `pwd` | Print working directory |
| `mkdir -p` | Create directory (and parents if needed) |
| `rm -rf` | Remove file or directory (Recursive & Force) |
| `cp -r` | Copy directory recursively |
| `mv` | Move or rename file/directory |

## System Monitoring

```bash
top / htop       # View processes and CPU/RAM usage
```
```bash
df -h            # View disk space usage
```
```bash
free -m          # View memory usage
```
```bash
uptime           # View system uptime and load average
```
## Permissions & Ownership

```bash
chmod 755 file    # Change permissions
```
```bash
chown user:group  # Change owner and group
```
```bash
sudo <command>    # Execute with superuser privileges
```
## Networking

```bash
ip addr           # View IP addresses
```
```bash
ping <host>       # Check connectivity
```
```bash
curl -I <url>     # Get HTTP headers
```
```bash
netstat -tuln     # View listening ports
```
## Archive & Compression

```bash
tar -czvf archive.tar.gz folder/ # Compress
```
```bash
tar -xzvf archive.tar.gz          # Decompress
```
```bash
unzip file.zip                    # Unzip
```
## Useful CLI Shortcuts

- `Ctrl + R`: Search command history.
- `Tab`: Auto-complete file/command names.
- `!!`: Run the last command again.
- `Alt + .`: Insert the last argument of the previous command.


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
