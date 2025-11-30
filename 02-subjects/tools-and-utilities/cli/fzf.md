---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: fzf
description: Fuzzy finder for command line
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/junegunn/fzf
---

# 🔍 fzf

A command-line fuzzy finder - interactive filter for any list.

## Features

- Lightning fast fuzzy search
- Works with any list input
- Shell integration (Ctrl-R, Ctrl-T, Alt-C)
- Vim integration
- Preview window support
- Multi-select capability

## Installation

```bash
brew install fzf

# Install shell key bindings and completion
$(brew --prefix)/opt/fzf/install
```

## Key Bindings (after install)

- `Ctrl-R` - Search command history
- `Ctrl-T` - Search files and directories
- `Alt-C` - cd into selected directory

## Common Usage

```bash
# Find and open file with vim
vim $(fzf)

# Kill process interactively
kill -9 $(ps aux | fzf | awk '{print $2}')

# Search git branches and checkout
git checkout $(git branch | fzf)

# Preview files with bat
fzf --preview 'bat --color=always {}'

# Search and cd
cd $(find . -type d | fzf)
```

## With Other Tools

```bash
# Combine with ripgrep
rg --files | fzf

# Combine with fd
fd --type f | fzf

# Git log search
git log --oneline | fzf --preview 'git show {1}'
```

## Related

- [[ripgrep|ripgrep]] - Fast grep alternative
- [[02-subjects/tools-and-utilities/cli/fd|fd]] - Fast find alternative
- [[02-subjects/tools-and-utilities/cli/bat|bat]] - Preview files

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
