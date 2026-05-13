# Linux Post-Installation Setup

Configuring your Linux system for a premium developer experience.

## 1. System Updates
```bash
sudo apt update && sudo apt upgrade -y
```
## 2. Essential Build Tools
```bash
sudo apt install build-essential git curl wget vim htop -y
```
## 3. Zsh & Oh My Zsh (Better Terminal)
```bash
sudo apt install zsh -y
```
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
## 4. SSH Key Generation
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
```bash
cat ~/.ssh/id_ed25519.pub # Copy this to GitHub/GitLab
```
## 5. Aliases & Environment Variables
Edit `~/.bashrc` or `~/.zshrc`:
```bash
alias ll='ls -alF'
```
```bash
alias gs='git status'
```
```bash
export EDITOR='vim'
```
## 6. Docker (Standard for Devs)
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```
```bash
sudo sh get-docker.sh
```
```bash
sudo usermod -aG docker $USER
```
## Recommended Folder Structure
```text
$HOME/
├── code/         # All development projects
├── tools/        # Manual binary installs
├── docs/         # Personal documentation
└── .config/      # Application configurations (Dotfiles)
```
> [!IMPORTANT]
> Always enable the firewall: `sudo ufw enable` and only allow necessary ports.


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
