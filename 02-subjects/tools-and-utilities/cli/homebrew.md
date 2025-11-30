---
creation date: 2024-11-04 13:30
tags:
  - shell/cli
  - shell/package-manager
  - macos
command: brew
description: The missing package manager for macOS and Linux
os:
  - linux
  - macos
source: Installed from website
url: https://brew.sh
---

# 🍺 Homebrew

The missing package manager for macOS and Linux - install, update, and manage software with ease.

## Features

- Simple package installation
- Automatic dependency resolution
- Version management
- Cask support for GUI apps
- Tap system for third-party repositories
- Easy updates and upgrades
- Bundle files for reproducible setups
- Cross-platform (macOS and Linux)

## Installation

```bash
# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Add to PATH (follow the instructions after installation)
# macOS Intel
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile

# macOS Apple Silicon
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile

# Linux
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.profile
```

## Common Usage

### Formulae (CLI Tools)

```bash
# Search for packages
brew search git
brew search /^git$/  # Regex search

# Get info about a package
brew info git

# Install package
brew install git

# Install specific version
brew install git@2.39

# Uninstall package
brew uninstall git

# List installed packages
brew list

# List installed formulae only
brew list --formula

# Show package dependencies
brew deps git
brew deps --tree git  # Tree format
```

### Casks (GUI Applications)

```bash
# Search for casks
brew search --cask chrome

# Install cask
brew install --cask google-chrome

# Uninstall cask
brew uninstall --cask google-chrome

# List installed casks
brew list --cask

# Reinstall cask
brew reinstall --cask google-chrome
```

### Updates and Maintenance

```bash
# Update Homebrew itself
brew update

# Upgrade all packages
brew upgrade

# Upgrade specific package
brew upgrade git

# Check for outdated packages
brew outdated

# Cleanup old versions
brew cleanup

# Cleanup specific package
brew cleanup git

# See what cleanup would remove (dry run)
brew cleanup -n
```

## Configuration

### Environment Variables

Add to `~/.zshrc` or `~/.config/homebrew/brew.env`:

```bash
# Install casks to ~/Applications instead of /Applications
export HOMEBREW_CASK_OPTS="--appdir=~/Applications"

# Use bat for brew cat command
export HOMEBREW_BAT=1

# Prevent insecure redirects
export HOMEBREW_NO_INSECURE_REDIRECT=1

# Auto-update before install/upgrade
export HOMEBREW_AUTO_UPDATE_SECS=86400  # Once per day

# Don't send analytics
export HOMEBREW_NO_ANALYTICS=1

# Use GitHub API token (for higher rate limits)
export HOMEBREW_GITHUB_API_TOKEN=your_token_here
```

### Brewfile

Create `~/Brewfile` for reproducible setups:

```ruby
# Taps
tap "homebrew/cask"
tap "homebrew/cask-fonts"

# CLI tools
brew "git"
brew "neovim"
brew "tmux"
brew "fzf"
brew "ripgrep"
brew "bat"
brew "eza"
brew "zoxide"

# Development tools
brew "node"
brew "python@3.11"
brew "go"

# GUI applications
cask "visual-studio-code"
cask "google-chrome"
cask "iterm2"
cask "docker"

# Fonts
cask "font-jetbrains-mono-nerd-font"

# Mac App Store apps (requires mas)
brew "mas"
mas "1Password", id: 1333542190
```

```bash
# Install from Brewfile
brew bundle

# Install from specific file
brew bundle --file=~/dotfiles/Brewfile

# Check if Brewfile dependencies are satisfied
brew bundle check

# Clean up packages not in Brewfile
brew bundle cleanup

# Generate Brewfile from installed packages
brew bundle dump
```

## Advanced Usage

### Taps (Third-party Repositories)

```bash
# List taps
brew tap

# Add tap
brew tap homebrew/cask-fonts

# Remove tap
brew untap homebrew/cask-fonts

# Search within tap
brew search homebrew/cask-fonts/
```

### Services

```bash
# List services
brew services list

# Start service
brew services start postgresql

# Stop service
brew services stop postgresql

# Restart service
brew services restart postgresql

# Run service without auto-start on login
brew services run postgresql
```

### Pinning Versions

```bash
# Pin package (prevent upgrades)
brew pin node@18

# Unpin package
brew unpin node@18

# List pinned packages
brew list --pinned
```

### Multiple Versions

```bash
# Install multiple versions
brew install node@18
brew install node@20

# Switch versions
brew unlink node@20
brew link node@18

# Link with force
brew link --force node@18
```

## Maintenance Script

Add to `~/.zshrc`:

```zsh
function bruc() {
  echo "Starting Homebrew maintenance..."

  # Update Homebrew
  if brew update; then
    echo "✅ Homebrew updated successfully."
  else
    echo "❌ Error: Homebrew update failed." >&2
    return 1
  fi

  # Upgrade installed packages
  if brew upgrade; then
    echo "✅ Homebrew packages upgraded successfully."
  else
    echo "❌ Error: Homebrew upgrade failed." >&2
    return 1
  fi

  # Cleanup old versions
  if brew cleanup; then
    echo "✅ Homebrew cleanup completed successfully."
  else
    echo "❌ Error: Homebrew cleanup failed." >&2
    return 1
  fi

  echo "✨ Homebrew maintenance completed."
}
```

## Troubleshooting

### Common Issues

**Permissions errors:**
```bash
# Fix Homebrew permissions
sudo chown -R $(whoami) /usr/local/Cellar /usr/local/Homebrew

# Or on Apple Silicon
sudo chown -R $(whoami) /opt/homebrew
```

**Broken symlinks:**
```bash
# Check for issues
brew doctor

# Fix broken symlinks
brew link --overwrite <package>
```

**Outdated packages:**
```bash
# Check what's outdated
brew outdated

# Update and upgrade all
brew update && brew upgrade
```

**Cleanup disk space:**
```bash
# See what will be cleaned
brew cleanup -n

# Clean up everything
brew cleanup -s

# Clean up old downloads
rm -rf ~/Library/Caches/Homebrew/*
```

**Reset Homebrew:**
```bash
# Reinstall Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Useful Commands

```bash
# Show installed package files
brew list git

# Open package homepage
brew home git

# Edit package formula
brew edit git

# Create formula
brew create https://example.com/foo-1.0.tar.gz

# Audit formula
brew audit git

# Test formula
brew test git

# Show analytics data
brew analytics

# Disable analytics
brew analytics off
```

## Tips

- Use Brewfile for reproducible setups
- Run `brew update && brew upgrade` regularly
- Use `brew cleanup` to free disk space
- Pin critical package versions with `brew pin`
- Use taps for specialized software
- Check `brew doctor` when having issues
- Use `brew info` before installing to see dependencies
- Set `HOMEBREW_NO_ANALYTICS=1` for privacy
- Use `--cask` flag explicitly for GUI apps
- Create aliases for common operations

## Useful Aliases

```bash
# Update and upgrade
alias bup='brew update && brew upgrade'

# Update, upgrade, and cleanup
alias bupc='brew update && brew upgrade && brew cleanup'

# Search both formulae and casks
alias bs='brew search'

# Install with verbose output
alias bi='brew install'
alias bic='brew install --cask'

# List installed
alias bl='brew list'
alias blc='brew list --cask'

# Cleanup
alias bclean='brew cleanup'

# Doctor
alias bd='brew doctor'
```

## Workflows

### Setting Up New Machine

```bash
# 1. Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Clone dotfiles
git clone https://github.com/user/dotfiles ~/dotfiles

# 3. Install from Brewfile
cd ~/dotfiles
brew bundle

# 4. Run configuration scripts
./setup.sh
```

### Regular Maintenance

```bash
# Weekly maintenance
brew update
brew upgrade
brew cleanup
brew doctor

# Or use the bruc function
bruc
```

### Removing Package

```bash
# Remove package and its dependencies
brew uninstall <package>
brew autoremove

# Force remove (ignore dependencies)
brew uninstall --force <package>
```

## Integration

### With Git

```bash
# Keep Brewfile in version control
cd ~/dotfiles
git add Brewfile
git commit -m "Update Brewfile"
git push
```

### With Neovim/Vim

```vim
" Install LSP servers with Homebrew
" brew install lua-language-server
" brew install typescript-language-server
```

### With Automation

```bash
# Cron job for auto-update (daily at 3 AM)
0 3 * * * /opt/homebrew/bin/brew update && /opt/homebrew/bin/brew upgrade
```

## Security

```bash
# Check for security vulnerabilities
brew audit --online

# Update to patch vulnerabilities
brew update && brew upgrade

# Verify package integrity
brew info --json <package> | jq

# Use specific versions for reproducibility
brew install node@18
brew pin node@18
```

## Related

- [[mas|mas]] - Mac App Store CLI (works with Brewfile)
- [[02-subjects/tools-and-utilities/cli/docker|Docker]] - Often installed via Homebrew
- [[02-subjects/tools-and-utilities/cli/git|Git]] - Version control, managed by Homebrew
- [[02-subjects/tools-and-utilities/cli/nix|Nix]] - Alternative package manager

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
