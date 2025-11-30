---
creation date: 2025-11-29
tags:
  - desktop/app
  - editor
  - dev/tools
description: High-performance multiplayer code editor
os:
  - macos
  - linux
source: Homebrew
url: https://zed.dev
---

# ⚡ Zed

A high-performance, multiplayer code editor from the creators of Atom and Tree-sitter.

## Features

- Extremely fast (written in Rust)
- Collaborative editing (like Google Docs for code)
- AI-powered (integrated GPT-4, etc.)
- Modern UI
- Git integration
- LSP support
- Vim mode
- Extension system
- Instant startup

## Installation

```bash
brew install --cask zed
```

## Key Features

### Performance
- Instant startup
- Smooth scrolling on large files
- Handles monorepos well
- GPU-accelerated rendering

### Collaboration
- Real-time collaborative editing
- Voice channels
- Screen sharing
- Shared projects

### AI Integration
- Inline completions
- Chat with AI
- Code generation
- Refactoring suggestions

### Language Support
- LSP for all major languages
- Tree-sitter syntax highlighting
- Integrated formatters
- Linters

## Key Bindings

```
Cmd+P          - Quick open
Cmd+Shift+P    - Command palette
Cmd+/          - Toggle comment
Cmd+D          - Add selection to next match
Cmd+K Cmd+B    - Toggle sidebar
Cmd+`          - Toggle terminal
```

## Configuration

Settings location: `~/.config/zed/settings.json`

```json
{
  "theme": "One Dark",
  "ui_font_size": 16,
  "buffer_font_size": 14,
  "buffer_font_family": "JetBrains Mono",
  "vim_mode": true,
  "format_on_save": "on",
  "tab_size": 2,
  "soft_wrap": "preferred_line_length",
  "preferred_line_length": 100,
  "telemetry": {
    "diagnostics": false,
    "metrics": false
  }
}
```

## Vim Mode

```json
{
  "vim_mode": true,
  "relative_line_numbers": true
}
```

## AI Features

```
Cmd+Enter      - Generate code
Cmd+Shift+A    - Open AI assistant
```

Configure AI:
```json
{
  "assistant": {
    "default_model": {
      "provider": "openai",
      "model": "gpt-4"
    }
  }
}
```

## Collaboration

1. **Start collaboration:**
   - Cmd+Shift+P → "Collaborate"
   - Share link with teammates

2. **Join collaboration:**
   - Click shared link or
   - Cmd+Shift+P → "Join Channel"

3. **Features:**
   - Real-time editing
   - Follow collaborators
   - Voice chat
   - Screen sharing

## Extensions

Install from Extensions panel:
- Language servers
- Themes
- Custom keybindings

## Terminal

```
Cmd+`          - Toggle terminal
Cmd+Shift+`    - New terminal
```

## Git Integration

- Inline blame
- Diff view
- Stage/unstage changes
- Commit from editor

## Project Management

```
Cmd+Shift+O    - Open project
Cmd+K Cmd+N    - New project
```

## vs VS Code

**Advantages:**
- Much faster
- Lower resource usage
- Better performance on large files
- Native multiplayer
- Cleaner UI

**Disadvantages:**
- Fewer extensions
- Newer/less mature
- Missing some VS Code features

## vs Vim/Neovim

**Advantages:**
- Modern GUI
- Built-in LSP setup
- Collaboration features
- AI integration
- Easier to configure

**Disadvantages:**
- Not as customizable
- Vim mode not 100% compatible
- Different philosophy

## Language-Specific Setup

### Python
```json
{
  "languages": {
    "Python": {
      "format_on_save": "on",
      "formatter": "language_server"
    }
  }
}
```

### JavaScript/TypeScript
```json
{
  "languages": {
    "TypeScript": {
      "tab_size": 2,
      "format_on_save": "on"
    }
  }
}
```

## Related

- [[02-subjects/tools-and-utilities/desktop/vscode|VS Code]] - Microsoft's editor
- [[04-archive/newvault/software/shell-app/nvim|Neovim]] - Terminal-based editor
- [[cursor]] - AI-first editor fork of VS Code

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
