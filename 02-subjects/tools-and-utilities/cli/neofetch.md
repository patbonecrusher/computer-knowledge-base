---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: neofetch
description: System information tool
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/dylanaraps/neofetch
---

# 💻 neofetch

A command-line system information tool that displays information about your system in a visually pleasing way.

## Features

- ASCII art logo of your OS
- System information display
- Highly customizable
- Fast and lightweight
- Screenshot capability
- Great for showing off your setup

## Installation

```bash
brew install neofetch
```

## Usage

```bash
# Basic usage
neofetch

# Customize output
neofetch --config ~/.config/neofetch/config.conf

# Show only specific info
neofetch --off

# ASCII distro logo options
neofetch --ascii_distro macos
neofetch --ascii_distro arch

# Screenshot mode
neofetch --screenshot

# No colors
neofetch --color_blocks off
```

## What It Shows

- OS
- Host/Model
- Kernel version
- Uptime
- Package count
- Shell
- Resolution
- DE (Desktop Environment)
- WM (Window Manager)
- Terminal
- CPU
- GPU
- Memory

## Configuration

```bash
# Edit config
$EDITOR ~/.config/neofetch/config.conf
```

Example customizations:
```bash
# Show/hide info
print_info() {
    info title
    info underline

    info "OS" distro
    info "Host" model
    info "Kernel" kernel
    info "Uptime" uptime
    info "Packages" packages
    info "Shell" shell
    info "Terminal" term
    info "CPU" cpu
    info "Memory" memory
}

# Colors
colors=(4 4 4 4 4 7)

# ASCII art
image_backend="ascii"
ascii_distro="auto"
```

## Common Uses

```bash
# Add to shell startup for cool terminal greeting
echo "neofetch" >> ~/.zshrc

# Show in SSH sessions
if [ -n "$SSH_CLIENT" ]; then
    neofetch
fi

# Take screenshot of your setup
neofetch --screenshot
```

## Related

- [[macchina|macchina]] - Faster alternative in Rust
- [[fastfetch|fastfetch]] - Even faster alternative

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
