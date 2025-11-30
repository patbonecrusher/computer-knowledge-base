---
creation date: 2024-11-04 13:30
tags:
  - shell/multiplexer
  - shell/cli
  - productivity
command: tmux
description: Terminal multiplexer for managing multiple terminal sessions
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/tmux/tmux/wiki
---

# 📺 tmux

Terminal multiplexer - split terminals, detach/reattach sessions, and manage multiple terminal sessions with ease.

## Features

- Multiple windows in a single terminal
- Split windows into panes
- Detachable sessions (survive SSH disconnects)
- Session sharing and pairing
- Customizable key bindings
- Plugin system
- Scriptable and automatable
- Copy mode with vi/emacs bindings

## Installation

```bash
# macOS
brew install tmux

# Linux
sudo apt install tmux      # Debian/Ubuntu
sudo yum install tmux      # RHEL/CentOS
```

## Common Usage

### Basic Commands

```bash
# Start new session
tmux

# Start new named session
tmux new -s mysession

# List sessions
tmux ls

# Attach to session
tmux attach -t mysession
tmux a -t mysession  # Short form

# Attach to last session
tmux attach

# Kill session
tmux kill-session -t mysession

# Kill all sessions
tmux kill-server
```

## Key Bindings

**Prefix key:** `Ctrl-b` (default) - Press before any command

### Sessions

- `Prefix + d` - Detach from session
- `Prefix + $` - Rename session
- `Prefix + s` - List and switch sessions
- `Prefix + (` - Switch to previous session
- `Prefix + )` - Switch to next session

### Windows

- `Prefix + c` - Create new window
- `Prefix + ,` - Rename window
- `Prefix + &` - Kill window
- `Prefix + n` - Next window
- `Prefix + p` - Previous window
- `Prefix + 0-9` - Switch to window by number
- `Prefix + w` - List windows
- `Prefix + f` - Find window

### Panes

- `Prefix + %` - Split horizontally (left/right)
- `Prefix + "` - Split vertically (top/bottom)
- `Prefix + o` - Switch to next pane
- `Prefix + ;` - Switch to last active pane
- `Prefix + x` - Kill pane
- `Prefix + !` - Break pane into window
- `Prefix + z` - Zoom/unzoom pane (fullscreen)
- `Prefix + {` - Move pane left
- `Prefix + }` - Move pane right
- `Prefix + Ctrl-o` - Rotate panes
- `Prefix + Space` - Cycle pane layouts

### Navigation

- `Prefix + ←↑→↓` - Move between panes
- `Prefix + q` - Show pane numbers (press number to jump)

### Copy Mode

- `Prefix + [` - Enter copy mode
- `Space` - Start selection
- `Enter` - Copy selection
- `Prefix + ]` - Paste
- `q` - Exit copy mode

### Other

- `Prefix + ?` - List all key bindings
- `Prefix + :` - Enter command mode
- `Prefix + t` - Show clock

## Configuration

Config file: `~/.tmux.conf`

### Basic Configuration

```bash
# Set prefix to Ctrl-a (more convenient than Ctrl-b)
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Enable mouse support
set -g mouse on

# Start windows and panes at 1, not 0
set -g base-index 1
setw -g pane-base-index 1

# Automatically renumber windows
set -g renumber-windows on

# Increase scrollback buffer
set -g history-limit 10000

# Enable vi mode
setw -g mode-keys vi

# Reduce escape time (helps with vim)
set -sg escape-time 0

# Enable 256 colors
set -g default-terminal "screen-256color"
set -ga terminal-overrides ",*256col*:Tc"

# Set window notifications
setw -g monitor-activity on
set -g visual-activity on

# Reload config
bind r source-file ~/.tmux.conf \; display "Config reloaded!"
```

### Better Key Bindings

```bash
# Split panes with | and -
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"
unbind '"'
unbind %

# Switch panes with Alt-arrow without prefix
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Resize panes with Ctrl-arrow
bind -r C-Left resize-pane -L 5
bind -r C-Right resize-pane -R 5
bind -r C-Up resize-pane -U 5
bind -r C-Down resize-pane -D 5

# Vi copy mode bindings
bind -T copy-mode-vi v send -X begin-selection
bind -T copy-mode-vi y send -X copy-pipe-and-cancel "pbcopy"
bind -T copy-mode-vi MouseDragEnd1Pane send -X copy-pipe-and-cancel "pbcopy"
```

### Status Bar Customization

```bash
# Status bar
set -g status on
set -g status-interval 1
set -g status-position bottom
set -g status-justify left

# Status bar colors
set -g status-style 'bg=#1e1e2e fg=#cdd6f4'

# Left status
set -g status-left '#[bg=#89b4fa,fg=#1e1e2e,bold] #S #[bg=#1e1e2e] '
set -g status-left-length 50

# Right status
set -g status-right '#[fg=#cdd6f4]%Y-%m-%d #[fg=#89b4fa,bold]%H:%M '
set -g status-right-length 50

# Window status
setw -g window-status-format ' #I:#W '
setw -g window-status-current-format '#[bg=#89b4fa,fg=#1e1e2e,bold] #I:#W '

# Pane border
set -g pane-border-style 'fg=#313244'
set -g pane-active-border-style 'fg=#89b4fa'
```

## Advanced Usage

### Sessions Management

```bash
# Create session with windows
tmux new-session -s dev -n editor
tmux split-window -h
tmux new-window -n console
tmux attach -t dev

# Scripted session setup
#!/bin/bash
tmux new-session -d -s dev
tmux send-keys -t dev 'cd ~/project' C-m
tmux send-keys -t dev 'nvim' C-m
tmux split-window -h -t dev
tmux send-keys -t dev 'npm run dev' C-m
tmux attach -t dev
```

### Tmux Plugin Manager (TPM)

```bash
# Install TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# Add to ~/.tmux.conf
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @plugin 'tmux-plugins/tmux-yank'

# Initialize TPM (must be at bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

# Install plugins: Prefix + I
# Update plugins: Prefix + U
# Uninstall plugins: Prefix + alt + u
```

### Useful Plugins

**tmux-resurrect** - Save and restore sessions:
```bash
set -g @plugin 'tmux-plugins/tmux-resurrect'

# Save: Prefix + Ctrl-s
# Restore: Prefix + Ctrl-r
```

**tmux-continuum** - Automatic save/restore:
```bash
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @continuum-restore 'on'
set -g @continuum-save-interval '15'  # minutes
```

**tmux-yank** - Better clipboard:
```bash
set -g @plugin 'tmux-plugins/tmux-yank'
```

**catppuccin theme**:
```bash
set -g @plugin 'catppuccin/tmux'
set -g @catppuccin_flavour 'mocha'
```

## Workflows

### Development Workflow

```bash
# Create development session
tmux new -s dev

# Window 1: Editor (default)
# Split for terminal
Prefix + %

# Window 2: Server
Prefix + c
Prefix + , (rename to "server")

# Window 3: Git
Prefix + c
Prefix + , (rename to "git")

# Navigate with Prefix + 0-9
```

### Remote Server Workflow

```bash
# SSH and create persistent session
ssh user@server
tmux new -s work

# Work normally, then detach
Prefix + d

# Later, reconnect
ssh user@server
tmux attach -t work
```

### Pairing Session

```bash
# User 1 creates session
tmux new -s pair

# User 2 attaches (read-write)
tmux attach -t pair

# Or read-only
tmux attach -t pair -r
```

## Integration

### With Neovim/Vim

```vim
" Navigate seamlessly between vim and tmux splits
" Install vim-tmux-navigator plugin
```

### With Zsh/Bash

```bash
# Auto-attach to tmux on shell start
if command -v tmux &> /dev/null && [ -z "$TMUX" ]; then
  tmux attach -t default || tmux new -s default
fi
```

### With FZF

```bash
# Fuzzy find and switch tmux sessions
bind-key s run-shell "tmux list-sessions -F '#S' | fzf | xargs tmux switch-client -t"
```

## Command Line Usage

```bash
# Send commands to session
tmux send-keys -t mysession "echo hello" C-m

# Create complex layouts
tmux new-session -d -s mylayout
tmux split-window -h
tmux split-window -v
tmux select-pane -t 0
tmux split-window -v
tmux attach -t mylayout

# Capture pane content
tmux capture-pane -t mysession:1.0 -p

# List all windows in all sessions
tmux list-windows -a
```

## Troubleshooting

### Colors not working

```bash
# Add to ~/.zshrc or ~/.bashrc
export TERM=xterm-256color

# Add to ~/.tmux.conf
set -g default-terminal "screen-256color"
set -ga terminal-overrides ",*256col*:Tc"
```

### Vim escape delay

```bash
# Add to ~/.tmux.conf
set -sg escape-time 0
```

### Mouse scrolling

```bash
# Enable mouse mode in ~/.tmux.conf
set -g mouse on
```

### Clipboard not working

```bash
# macOS
brew install reattach-to-user-namespace

# Add to ~/.tmux.conf
set -g default-command "reattach-to-user-namespace -l $SHELL"

# Or use tmux-yank plugin
set -g @plugin 'tmux-plugins/tmux-yank'
```

## Tips

- Use meaningful session names for easy identification
- Create shell scripts to set up common session layouts
- Use mouse mode for quick navigation (once enabled)
- Zoom panes (`Prefix + z`) for focused work
- Use copy mode to scroll and search terminal history
- Pair tmux with a good terminal (iTerm2, Alacritty, Warp)
- Learn a few key bindings well rather than all at once
- Use TPM plugins to extend functionality
- Remap prefix to `Ctrl-a` - easier to press
- Use `|` and `-` for splits - more intuitive

## Common Patterns

### Quick Dev Setup Script

```bash
#!/bin/bash
# dev-session.sh
SESSION="dev"

tmux has-session -t $SESSION 2>/dev/null

if [ $? != 0 ]; then
  # Create session
  tmux new-session -d -s $SESSION -n editor

  # Editor window
  tmux send-keys -t $SESSION:editor "cd ~/project && nvim" C-m

  # Console window
  tmux new-window -t $SESSION -n console
  tmux send-keys -t $SESSION:console "cd ~/project" C-m

  # Server window
  tmux new-window -t $SESSION -n server
  tmux send-keys -t $SESSION:server "cd ~/project && npm run dev" C-m

  # Select first window
  tmux select-window -t $SESSION:editor
fi

tmux attach -t $SESSION
```

## Related

- [[zellij|Zellij]] - Modern tmux alternative
- [[screen|GNU Screen]] - Older terminal multiplexer
- [[wezterm|WezTerm]] - Terminal with built-in multiplexing
- [[byobu|Byobu]] - Tmux wrapper with enhancements

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
