---
creation date: 2024-12-30 10:21
tags:
  - shell/cli
  - shell/navigation
  - file-manager
command: yazi
description: Blazing fast terminal file manager written in Rust
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/sxyazi/yazi
---

# 🗂️ Yazi

Blazing fast terminal file manager written in Rust - navigate directories, preview files, and manage your filesystem with speed.

## Features

- Blazing fast async I/O
- Full async support
- Powerful file preview
- Built-in code highlighter
- Image preview in terminal
- Vim-like modal keybindings
- Multi-tab interface
- Bulk file operations
- File search and filter
- Customizable and plugin support
- Cross-platform (Linux, macOS, Windows)

## Installation

```bash
# macOS
brew install yazi

# Install optional dependencies for better previews
brew install ffmpegthumbnailer
brew install unar
brew install jq
brew install poppler
brew install fd
brew install ripgrep
brew install fzf
brew install zoxide
```

## Common Usage

```bash
# Open yazi in current directory
yazi

# Open in specific directory
yazi /path/to/dir

# Open and change directory on exit
function ya() {
    local tmp="$(mktemp -t "yazi-cwd.XXXXX")"
    yazi "$@" --cwd-file="$tmp"
    if cwd="$(cat -- "$tmp")" && [ -n "$cwd" ] && [ "$cwd" != "$PWD" ]; then
        cd -- "$cwd"
    fi
    rm -f -- "$tmp"
}
```

## Key Bindings

### Navigation

- `j/k` - Move down/up
- `h/l` - Go to parent/child directory
- `g` - Go to top
- `G` - Go to bottom
- `Ctrl-u/d` - Half page up/down
- `Ctrl-b/f` - Full page up/down
- `/` - Search in current directory
- `n/N` - Next/previous search result

### File Operations

- `Space` - Toggle selection
- `v` - Enter visual mode (select multiple)
- `V` - Enter visual mode (select all)
- `Ctrl-a` - Select all
- `Ctrl-r` - Inverse selection
- `y` - Yank (copy) files
- `x` - Cut files
- `p` - Paste files
- `d` - Delete selected files
- `r` - Rename file
- `a` - Create file
- `o` - Open file
- `O` - Open file interactively (choose app)

### Tabs

- `t` - Create new tab
- `Tab` - Switch to next tab
- `Shift-Tab` - Switch to previous tab
- `1-9` - Switch to tab by number
- `[/]` - Switch to previous/next tab
- `w` - Close current tab

### Operations

- `.` - Toggle hidden files
- `s` - Sort files
- `z` - Jump to directory (with zoxide)
- `f` - Filter files
- `F` - Find files (with fd/fzf)
- `~` - Go to home directory
- `-` - Go to previous directory
- `:` - Enter command mode
- `Esc` - Cancel/Go back
- `q` - Quit

### Preview

- `i` - Toggle preview
- `I` - Maximize preview
- `e` - Edit file
- `E` - Edit file with custom editor

### Help

- `?` - Show help
- `F1` - View keybindings

## Configuration

Config directory: `~/.config/yazi/`

### Main Config (`yazi.toml`)

```toml
[manager]
# Show hidden files by default
show_hidden = true

# Sort settings
sort_by = "modified"
sort_reverse = true
sort_dir_first = true

# Layout
ratio = [1, 4, 3]
linemode = "size"

[preview]
# Image preview
image_preview = true

# Maximum preview size
max_width = 600
max_height = 900

# Tab width
tab_size = 4

[opener]
# Default openers
edit = [
    { exec = 'nvim "$@"', block = true }
]
open = [
    { exec = 'open "$@"', desc = "Open with default app" }
]
reveal = [
    { exec = 'open -R "$@"', desc = "Reveal in Finder" }
]
```

### Keymap Config (`keymap.toml`)

```toml
[manager]
# Custom keybindings
keymap = [
    { on = ["<Esc>"], exec = "escape", desc = "Exit visual mode, clear selected, or cancel" },
    { on = ["q"], exec = "quit", desc = "Exit yazi" },
    { on = ["<C-q>"], exec = "close", desc = "Close current tab" },

    # Navigation
    { on = ["k"], exec = "arrow -1", desc = "Move cursor up" },
    { on = ["j"], exec = "arrow 1", desc = "Move cursor down" },
    { on = ["h"], exec = "leave", desc = "Go to parent directory" },
    { on = ["l"], exec = "enter", desc = "Enter directory" },

    # Custom shortcuts
    { on = ["g", "h"], exec = "cd ~", desc = "Go to home" },
    { on = ["g", "c"], exec = "cd ~/.config", desc = "Go to config" },
    { on = ["g", "d"], exec = "cd ~/Downloads", desc = "Go to Downloads" },
    { on = ["g", "D"], exec = "cd ~/Documents", desc = "Go to Documents" },
]
```

### Theme Config (`theme.toml`)

```toml
[flavor]
use = "mocha"  # catppuccin mocha theme

[manager]
# File type colors
cwd = { fg = "cyan" }
hovered = { reversed = true }
preview_hovered = { underline = true }

[status]
separator_style = { fg = "gray", bg = "gray" }

[input]
border = { fg = "blue" }
title = { fg = "white" }
value = { fg = "yellow" }
selected = { bg = "blue" }
```

## Advanced Usage

### Shell Integration

Add to `~/.zshrc` or `~/.bashrc`:

```bash
# Function to cd on exit
function ya() {
    local tmp="$(mktemp -t "yazi-cwd.XXXXX")"
    yazi "$@" --cwd-file="$tmp"
    if cwd="$(cat -- "$tmp")" && [ -n "$cwd" ] && [ "$cwd" != "$PWD" ]; then
        cd -- "$cwd"
    fi
    rm -f -- "$tmp"
}

# Keybinding to open yazi
bindkey -s '^o' 'ya\n'  # Ctrl-O opens yazi
```

### File Previews

Yazi automatically detects and previews:
- Images (with kitty/iTerm2 protocols)
- Videos (thumbnails with ffmpegthumbnailer)
- PDFs (with poppler)
- Archives (with unar)
- JSON (with jq)
- Code (syntax highlighting)
- Markdown (rendered)

### Bulk Operations

```bash
# In yazi:
# 1. Select files with Space or v (visual mode)
# 2. Press y to yank, x to cut
# 3. Navigate to destination
# 4. Press p to paste

# Delete multiple files
# 1. Select files
# 2. Press d
# 3. Confirm deletion
```

### Custom Openers

In `~/.config/yazi/yazi.toml`:

```toml
[opener]
# Open videos with IINA
video = [
    { exec = 'iina "$@"', orphan = true }
]

# Open images with Preview
image = [
    { exec = 'open -a Preview "$@"', orphan = true }
]

# Edit text files with Neovim
text = [
    { exec = 'nvim "$@"', block = true }
]

# Open PDFs with Skim
pdf = [
    { exec = 'open -a Skim "$@"', orphan = true }
]
```

## Integration

### With Zoxide

```bash
# Press 'z' in yazi to jump to frequently used directories
# Requires zoxide installed: brew install zoxide
```

### With FZF

```bash
# Press 'F' to find files with fzf
# Requires fzf installed: brew install fzf
```

### With Neovim

```lua
-- Install yazi.nvim plugin
-- Open yazi in Neovim with :Yazi
```

### With Tmux

```bash
# Open yazi in new tmux pane
bind-key -n C-o split-window -h "yazi"
```

## Workflows

### File Management

1. Navigate with `j/k/h/l`
2. Preview files automatically
3. Search with `/`
4. Select with `Space` or `v`
5. Copy/move with `y/x` then `p`
6. Delete with `d`

### Image Viewing

1. Navigate to image directory
2. Use arrow keys to browse
3. Press `i` to toggle preview size
4. Press `I` to maximize preview
5. Press `o` to open in external viewer

### Multi-Tab Organization

1. Press `t` to create new tab
2. Navigate to different directories
3. Use `Tab` to switch between tabs
4. Move files between tabs with copy/paste
5. Press `w` to close tabs

## Plugins

Yazi supports plugins in Lua. Place them in `~/.config/yazi/plugins/`

### Example: Jump to Git Root

```lua
-- ~/.config/yazi/plugins/git-root.yazi/init.lua
return {
    entry = function()
        local git_root = Command("git")
            :args({ "rev-parse", "--show-toplevel" })
            :stdout(Command.PIPED)
            :output()

        if git_root.status.success then
            local root = git_root.stdout:gsub("%s+", "")
            ya.manager_emit("cd", { root })
        end
    end,
}
```

Bind in `keymap.toml`:
```toml
{ on = ["g", "r"], exec = "plugin git-root", desc = "Go to git root" }
```

## Tips

- Use `ya` shell function to cd on exit
- Enable hidden files by default in config
- Use visual mode (`v`) for bulk operations
- Set up custom openers for your workflow
- Use tabs for organizing different tasks
- Press `.` to quickly toggle hidden files
- Use `z` with zoxide for fast directory jumping
- Configure preview settings for better performance
- Set up key bindings that match your muscle memory
- Use `f` to filter files in large directories

## Troubleshooting

### Images not previewing

```bash
# Check terminal supports image protocol
# Kitty and iTerm2 work best
# Or install sixel support

# Ensure preview is enabled in config
[preview]
image_preview = true
```

### Slow preview for large directories

```bash
# Disable preview or limit preview size
[preview]
max_width = 400
max_height = 600
```

### Keybindings not working

```bash
# Check keymap.toml syntax
# Restart yazi after config changes
```

## Related

- [[lf|lf]] - Terminal file manager in Go
- [[ranger|ranger]] - Python-based file manager
- [[nnn|nnn]] - Minimal file manager
- [[02-subjects/tools-and-utilities/cli/fd|fd]] - Fast find alternative (works with yazi)
- [[ripgrep|ripgrep]] - Fast grep (for searching)
- [[fzf|fzf]] - Fuzzy finder (integrates with yazi)
- [[02-subjects/tools-and-utilities/cli/zoxide|zoxide]] - Smarter cd (integrates with yazi)

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
