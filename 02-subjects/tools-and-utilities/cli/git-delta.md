---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
  - git
command: delta
description: Better diff viewer for git
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/dandavison/delta
---

# 🌈 git-delta

A syntax-highlighting pager for git, diff, and grep output.

## Features

- Syntax highlighting
- Side-by-side diffs
- Line numbers
- Git blame integration
- Word-level diff highlighting
- Customizable themes

## Installation

```bash
brew install git-delta
```

## Configuration

Add to `~/.gitconfig`:

```gitconfig
[core]
    pager = delta

[interactive]
    diffFilter = delta --color-only

[delta]
    navigate = true
    light = false
    side-by-side = true
    line-numbers = true

[merge]
    conflictstyle = diff3

[diff]
    colorMoved = default
```

## Usage

Once configured, delta automatically enhances:

```bash
# All these will use delta
git diff
git show
git log -p
git stash show -p
git blame
```

## Themes

```bash
# List available themes
delta --list-syntax-themes

# Try different themes
delta --show-syntax-themes

# Set in gitconfig
[delta]
    syntax-theme = Monokai Extended
```

## Features

- Navigate between diff sections with `n` and `N`
- Side-by-side view for easier comparison
- Automatic language detection for syntax highlighting
- Works with `git add -p` interactive mode

## Related

- [[02-subjects/tools-and-utilities/cli/git|Git]] - Version control
- [[02-subjects/tools-and-utilities/cli/lazygit|lazygit]] - Git TUI
- [[02-subjects/tools-and-utilities/cli/bat|bat]] - File viewer with syntax highlighting

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
