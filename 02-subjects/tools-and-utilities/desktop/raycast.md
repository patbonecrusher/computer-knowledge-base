---
creation date: 2025-11-29
tags:
  - desktop/app
  - productivity
  - macos
description: Extendable launcher and productivity tool
os:
  - macos
source: Homebrew
url: https://raycast.com
---

# ⚡ Raycast

A blazingly fast, totally extendable launcher that lets you complete tasks, calculate, share common links, and much more.

## Features

- Application launcher
- Window management
- Clipboard history
- Snippets
- Calculator
- File search
- Script commands
- Extensions ecosystem
- System commands
- Calendar integration

## Installation

```bash
brew install --cask raycast
```

## Key Features

### Launcher
- Cmd+Space (can replace Spotlight)
- Fuzzy search for apps, files, contacts
- Quick actions on results

### Clipboard History
- Persistent clipboard manager
- Search through history
- Pin favorites
- Organize into collections

### Snippets
- Text expansion
- Dynamic placeholders (date, time, etc.)
- Organize by collections
- Sync across devices

### Window Management
- Resize and position windows
- Predefined layouts
- Custom shortcuts
- Multi-monitor support

### Extensions
- 1Password integration
- GitHub
- Jira
- Notion
- Linear
- Slack
- And 1000+ more

## Common Commands

```
Open Raycast:        Cmd+Space
Search apps:         Type app name
Calculator:          Type equation (2+2)
Clipboard history:   Search "clipboard"
Window management:   Search "window"
System:              Search "sleep", "lock", etc.
```

## Useful Extensions

- **1Password** - Quick access to passwords
- **GitHub** - Search repos, issues, PRs
- **Brew** - Manage Homebrew packages
- **Kill Process** - Manage running processes
- **Color Picker** - Pick colors from screen
- **Speedtest** - Test internet speed
- **Timers** - Quick countdown timers

## Script Commands

Write custom commands in any language:

```bash
#!/bin/bash

# Required parameters:
# @raycast.schemaVersion 1
# @raycast.title Hello World
# @raycast.mode compact

echo "Hello from Raycast!"
```

## Hotkeys

Setup custom hotkeys for:
- Clipboard history
- Snippets
- Window management
- Favorite commands

## vs Alfred/Spotlight

**Advantages over Spotlight:**
- Extensions
- Clipboard history
- Window management
- Snippets
- Better UI/UX

**Advantages over Alfred:**
- Free for most features
- Modern UI
- Better extension ecosystem
- Active development
- Native Swift app

## Pro Features

Free tier is very generous, Pro adds:
- Unlimited clipboard history
- Cloud sync
- AI commands
- Themes
- Pro extensions

## Related

- [[hammerspoon|Hammerspoon]] - Automation tool
- [[alfred]] - Alternative launcher

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
