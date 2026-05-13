# Installing Linux

Guide to choosing and installing a Linux distribution in 2026.

## Choosing a Distribution (Distro)

| Use Case | Recommended Distro |
| :--- | :--- |
| **Desktop / Beginner** | Ubuntu, Linux Mint, Pop!_OS |
| **Server** | Ubuntu Server, Debian, RHEL / Rocky Linux |
| **Developer / Enthusiast**| Fedora, Arch Linux |
| **Privacy / Security** | Tails, Qubes OS |

## Installation Methods

### 1. Live USB (Standard)
1.  Download the ISO from the distro's website.
2.  Flash to a USB drive using **Rufus** (Windows) or **BalenaEtcher** (macOS/Linux).
3.  Boot from USB and follow the graphical installer.

### 2. WSL 2 (Windows)
```bash
wsl --install -d Ubuntu
```
### 3. Virtual Machine
Use **VirtualBox** or **VMware Player** to run Linux inside your current OS.

## System Verification

```bash
lsb_release -a # Show distro info
```
```bash
uname -a        # Show kernel version
```
## Package Managers

- **Debian/Ubuntu**: `apt`
- **Fedora**: `dnf`
- **Arch**: `pacman`
- **Universal**: `flatpak`, `snap`

> [!TIP]
> Use **Ventoy** on your USB drive to boot multiple ISOs without re-flashing.


## Code Examples

### Find large files
```bash
find . -type f -size +100M -print
```
### Grep recursively (ripgrep)
```bash
rg "TODO|FIXME" -n .
```