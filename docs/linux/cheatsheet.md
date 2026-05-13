# Linux CLI Cheatsheet

Quick reference for common Linux commands and shortcuts.

## File Navigation & Management

| Task | Command |
| :--- | :--- |
| **Go to home** | `cd ~` |
| **Go up one level** | `cd ..` |
| **Search for file** | `find . -name "filename"` |
| **Search in text** | `grep -r "pattern" .` |
| **Count lines** | `wc -l file` |
| **Show file head** | `head -n 10 file` |
| **Show file tail** | `tail -f file` |

## System Info

```bash
whoami     # Current user
```
```bash
id         # Current user & group IDs
```
```bash
history    # Command history
```
```bash
date       # Current date & time
```
```bash
cal        # Calendar
```
## Redirects & Pipes

```bash
# Redirect output to file (overwrite)
```
```bash
command > file.txt
```
```bash
# Redirect output to file (append)
```
```bash
command >> file.txt
```
```bash
# Pipe output to another command
```
```bash
cat file.txt | grep "search"
```
```bash
# Redirect error to file
```
```bash
command 2> error.log
```
## Useful Keyboard Shortcuts

- `Ctrl + A`: Move cursor to beginning of line.
- `Ctrl + E`: Move cursor to end of line.
- `Ctrl + U`: Clear line before cursor.
- `Ctrl + K`: Clear line after cursor.
- `Ctrl + L`: Clear screen.
- `Ctrl + C`: Interrupt current process.
- `Ctrl + Z`: Suspend current process (use `fg` to resume).

## Help Commands

- `man <command>`: View the manual page.
- `<command> --help`: Quick help.
- `whatis <command>`: Short description.
- `tldr <command>`: Practical examples (requires tldr package).


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
