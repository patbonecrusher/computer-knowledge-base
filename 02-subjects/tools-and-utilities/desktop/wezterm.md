---
creation date: 2025-11-29
tags:
  - desktop/app
  - terminal
  - dev/tools
description: GPU-accelerated cross-platform terminal emulator
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://wezfurlong.org/wezterm/
---

# 💻 WezTerm

A GPU-accelerated cross-platform terminal emulator and multiplexer written in Rust.

## Features

- GPU acceleration
- Built-in terminal multiplexer
- Tabs and panes
- Ligature support
- Color schemes
- Image protocol support
- SSH integration
- Cross-platform
- Lua configuration

## Installation

```bash
brew install --cask wezterm
```

## Configuration

Config file: `~/.wezterm.lua`

```lua
local wezterm = require 'wezterm'

return {
  -- Color scheme
  color_scheme = "Tokyo Night",

  -- Font
  font = wezterm.font("JetBrains Mono"),
  font_size = 14.0,

  -- Window
  window_background_opacity = 0.95,
  window_decorations = "RESIZE",

  -- Tabs
  hide_tab_bar_if_only_one_tab = true,
  use_fancy_tab_bar = false,

  -- Keys
  keys = {
    { key = "d", mods = "CMD", action = wezterm.action.SplitHorizontal },
    { key = "d", mods = "CMD|SHIFT", action = wezterm.action.SplitVertical },
  },
}
```

## Multiplexing

Built-in, no need for tmux:

```
Cmd+D          - Split horizontally
Cmd+Shift+D    - Split vertically
Cmd+W          - Close pane
Cmd+[/]        - Navigate panes
Cmd+T          - New tab
Cmd+1-9        - Switch tabs
```

## Key Features

### GPU Acceleration
- Smooth scrolling
- Handles large buffers
- Efficient rendering

### Multiplexing
- Built-in panes and tabs
- No external multiplexer needed
- Domain/workspace support

### SSH Integration
```lua
ssh_domains = {
  {
    name = "my-server",
    remote_address = "server.example.com",
    username = "user",
  },
}
```

### Image Support
- Displays images inline
- Supports iTerm2 image protocol
- Sixel graphics

## Useful Commands

```bash
# Open config
wezterm show-keys

# List color schemes
wezterm ls-fonts

# SSH connection
wezterm ssh user@host
```

## Advanced Config

```lua
local wezterm = require 'wezterm'

return {
  -- Performance
  front_end = "WebGpu",
  max_fps = 120,

  -- Font features
  harfbuzz_features = { "calt=1", "clig=1", "liga=1" },

  -- Cursor
  default_cursor_style = "BlinkingBar",
  cursor_blink_rate = 500,

  -- Scrollback
  scrollback_lines = 10000,

  -- Colors
  colors = {
    cursor_bg = "#52ad70",
    cursor_fg = "black",
  },

  -- Padding
  window_padding = {
    left = 8,
    right = 8,
    top = 8,
    bottom = 8,
  },
}
```

## Domains

Organize work into domains:

```lua
unix_domains = {
  {
    name = "unix",
  },
}
```

## vs Other Terminals

**vs iTerm2:**
- Faster
- Cross-platform
- Built-in multiplexing
- Lua config (not GUI)

**vs Ghostty:**
- More features
- Better customization
- SSH support
- Image support

**vs Alacritty:**
- More features
- Built-in multiplexing
- Tabs
- More configuration options

**vs Kitty:**
- Cross-platform
- Different config style (Lua vs config file)
- Better documentation

## Performance Tips

```lua
-- Max performance config
return {
  front_end = "WebGpu",
  webgpu_power_preference = "HighPerformance",
  animation_fps = 60,
  max_fps = 120,
}
```

## Related

- [[02-subjects/tools-and-utilities/desktop/ghostty|Ghostty]] - Another modern terminal
- [[04-archive/newvault/software/shell-app/tmux|tmux]] - Terminal multiplexer (not needed with WezTerm)
- [[zellij|zellij]] - Modern terminal workspace

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
