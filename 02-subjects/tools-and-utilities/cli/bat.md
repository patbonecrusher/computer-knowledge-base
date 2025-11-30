---
creation date: 2025-01-02 14:21
tags:
  - shell/cli
  - dev/tools
command: bat
description: A cat clone with syntax highlighting and Git integration
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://github.com/sharkdp/bat
---

# 🦇 bat

A `cat` clone with wings - syntax highlighting, Git integration, and automatic paging.

## Features

- Syntax highlighting for many languages
- Git integration (shows modifications)
- Automatic paging
- File concatenation
- Line numbers
- Non-printable character display
- Themes support
- Works as a drop-in cat replacement

## Installation

```bash
brew install bat
```

## Common Usage

```bash
# View a file with syntax highlighting
bat file.py

# Show line numbers
bat -n file.py

# Show Git modifications
bat file.py

# View multiple files
bat file1.py file2.py

# Specify language
bat --language=python file.txt

# Plain output (no decorations)
bat -p file.py

# Show non-printable characters
bat -A file.txt

# Page through output
bat large-file.txt
```

## Configuration

Create config file at `~/.config/bat/config`:

```bash
# Set theme
--theme="TwoDark"

# Show line numbers
--style="numbers,changes,header"

# Use italic text
--italic-text=always

# Set pager
--pager="less -FR"
```

## Themes

```bash
# List available themes
bat --list-themes

# Preview a theme
bat --theme=Monokai file.py

# Set theme in config
echo '--theme="Dracula"' >> ~/.config/bat/config
```

## Integration

### Use as man pager
```bash
# In ~/.zshrc or ~/.bashrc
export MANPAGER="sh -c 'col -bx | bat -l man -p'"
export MANROFFOPT="-c"
```

### Use with fzf for preview
```bash
fzf --preview 'bat --color=always --style=numbers --line-range=:500 {}'
```

### Git diff
```bash
# Use bat for git diff
git config --global core.pager "bat --style=plain"
```

### Alias for cat
```bash
alias cat='bat --paging=never'
alias less='bat'
```

## Customization

### Custom Language
```bash
# Add to ~/.config/bat/syntaxes/
bat cache --build
```

### Color Scheme
```bash
# Use custom theme
bat --theme="GitHub"
```

## Common Aliases

```bash
# Quick view with line numbers
alias batn='bat --style=numbers'

# Plain output
alias batp='bat --style=plain'

# Full decorations
alias batf='bat --style=full'
```

## Related

- [[eza|eza]] - Modern ls with colors
- [[fzf|fzf]] - Fuzzy finder (works great with bat)
- [[ripgrep|ripgrep]] - Fast grep (often used with bat)
- [[git-delta|git-delta]] - Better git diff

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
