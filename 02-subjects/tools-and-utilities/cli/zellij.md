---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: zellij
description: Modern terminal workspace manager
os:
  - linux
  - macos
source: Homebrew
url: https://zellij.dev
---

# 🖥️ zellij

A terminal workspace manager - modern alternative to tmux with better defaults and UX.

## Features

- Built-in layouts
- Floating panes
- Plugin system
- Session management
- No configuration required
- Mouse support
- Collaborative sessions
- Better onboarding than tmux

## Installation

```bash
brew install zellij
```

## Basic Usage

```bash
# Start zellij
zellij

# Start with a layout
zellij --layout compact

# List sessions
zellij list-sessions

# Attach to session
zellij attach session-name

# Kill session
zellij kill-session session-name

# Kill all sessions
zellij kill-all-sessions
```

## Key Bindings

Zellij shows shortcuts at the bottom by default!

**Pane Mode** (`Ctrl-p`):
- `n` - New pane
- `x` - Close pane
- `f` - Toggle fullscreen
- `Arrow keys` - Navigate panes
- `z` - Toggle pane frames

**Tab Mode** (`Ctrl-t`):
- `n` - New tab
- `x` - Close tab
- `r` - Rename tab
- `Arrow keys` - Navigate tabs

**Resize Mode** (`Ctrl-n`):
- `Arrow keys` - Resize panes
- `+/-` - Increase/decrease size

**Session Mode** (`Ctrl-o`):
- `d` - Detach
- `w` - Session manager

## Layouts

Built-in layouts:
```bash
zellij --layout default
zellij --layout compact
zellij --layout strider  # File tree
```

Custom layout:
```kdl
// ~/.config/zellij/layouts/dev.kdl
layout {
    pane split_direction="vertical" {
        pane
        pane split_direction="horizontal" {
            pane
            pane
        }
    }
}
```

## Configuration

```bash
# Generate default config
zellij setup --dump-config > ~/.config/zellij/config.kdl

# Edit config
$EDITOR ~/.config/zellij/config.kdl
```

Example config:
```kdl
keybinds {
    shared_except "locked" {
        bind "Ctrl g" { SwitchToMode "Locked"; }
    }
}

theme {
    name "tokyo-night"
}

default_layout "compact"
```

## Plugins

```bash
# File manager
zellij --layout strider

# Session manager
# Ctrl-o w
```

## vs tmux

**Advantages:**
- Better discoverability (shows keybindings)
- No configuration needed to get started
- Modern UI
- Better defaults
- Floating panes
- Plugin system

**When to use tmux:**
- Need maximum compatibility
- Prefer established ecosystem
- Muscle memory with tmux

## Session Workflow

```bash
# Start named session
zellij -s project-name

# Detach (Ctrl-o d)

# List sessions
zellij ls

# Reattach
zellij attach project-name

# Or last session
zellij attach
```

## Related

- [[02-subjects/tools-and-utilities/cli/tmux|tmux]] - Traditional terminal multiplexer
- [[wezterm|WezTerm]] - Terminal with multiplexing built-in
- [[02-subjects/tools-and-utilities/cli/zoxide|zoxide]] - Smart directory jumper

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
