---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
  - macos
command: mas
description: Mac App Store command line interface
os:
  - macos
source: Homebrew
url: https://github.com/mas-cli/mas
---

# 🍎 mas

Command line interface for the Mac App Store - search, install, and update apps from the terminal.

## Features

- Install Mac App Store apps from CLI
- Update all apps
- Search for apps
- List installed apps
- Useful for automation and dotfiles

## Installation

```bash
brew install mas
```

## Common Usage

```bash
# List installed apps
mas list

# Search for an app
mas search Xcode

# Install an app (use app ID from search)
mas install 497799835

# Update all apps
mas upgrade

# Check for outdated apps
mas outdated

# Sign in (opens App Store)
mas signin email@example.com

# Sign out
mas signout

# Show account info
mas account
```

## Practical Examples

```bash
# Install Xcode
mas install 497799835

# Install multiple apps
mas install 497799835 1295203466 # Xcode and Microsoft Remote Desktop

# Update everything
mas upgrade

# List apps with IDs (useful for dotfiles)
mas list | sort
```

## Automation

Great for setting up new Macs:

```bash
#!/bin/bash
# install-mac-apps.sh

# Install from App Store
mas install 497799835  # Xcode
mas install 1295203466 # Microsoft Remote Desktop
mas install 441258766  # Magnet
mas install 1147396723 # WhatsApp

# Update all
mas upgrade
```

## Limitations

- Cannot install paid apps you haven't already purchased
- Some apps may not be available via mas
- Requires being signed into App Store

## Related

- [[02-subjects/tools-and-utilities/cli/homebrew|Homebrew]] - Package manager for macOS
- [[02-subjects/tools-and-utilities/cli/m-cli|m-cli]] - macOS CLI tools

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
