---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: eza
description: Modern replacement for ls
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/eza-community/eza
---

# 📂 eza

A modern, maintained replacement for `ls` with better defaults and more features.

## Features

- Color-coded file types
- Git integration (shows git status inline)
- Tree view built-in
- Icons support
- Better sorting options
- Hyperlink support for terminals
- Extended attributes display

## Installation

```bash
brew install eza
```

## Common Usage

```bash
# Basic listing with icons
eza --icons

# Long format with git status
eza -l --git

# Tree view
eza --tree

# All files including hidden
eza -a

# Common alias setup
alias ls="eza --icons"
alias ll="eza -l --icons --git"
alias la="eza -la --icons --git"
alias lt="eza --tree --icons"
```

## Advantages over ls

- Maintained (ls alternatives like exa are abandoned)
- Better colors and icons
- Built-in git awareness
- More intuitive flags
- Better performance on large directories

## Related

- [[02-subjects/tools-and-utilities/cli/fd|fd]] - Modern find alternative
- [[02-subjects/tools-and-utilities/cli/bat|bat]] - Modern cat alternative
- [[02-subjects/tools-and-utilities/cli/zoxide|zoxide]] - Smart cd replacement

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
