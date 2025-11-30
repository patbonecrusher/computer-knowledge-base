---
creation date: 2025-11-29
tags:
  - homebrew
  - software
  - sync
---

# 🍺 Homebrew Sync Summary

**Date**: 2025-11-29
**Status**: Complete ✅

Your vault has been synchronized with your Homebrew installations!

## Packages Scanned

- **Formulae (CLI tools)**: 221 packages
- **Casks (Desktop apps)**: 63 applications

## Documentation Created

### New CLI Tools Added (13)

1. **eza** - Modern replacement for `ls`
2. **fzf** - Fuzzy finder for command line
3. **gh** - GitHub official CLI tool
4. **git-delta** - Better diff viewer for git
5. **jq** - JSON processor
6. **mas** - Mac App Store CLI
7. **neofetch** - System information tool
8. **pre-commit** - Git hooks framework
9. **ripgrep (rg)** - Ultra-fast grep alternative
10. **tree** - Directory tree visualization
11. **zellij** - Modern terminal workspace manager
12. **thefuck** - Command corrector
13. **direnv** - Per-directory environment variables

### New Desktop Apps Added (5)

1. **Raycast** - Extendable launcher and productivity tool
2. **WezTerm** - GPU-accelerated terminal emulator
3. **Zed** - High-performance multiplayer code editor
4. **OrbStack** - Fast Docker & Linux VMs (Docker Desktop alternative)
5. **Hammerspoon** - macOS automation tool

## Current Documentation Stats

- **Total CLI tools**: 55 documented
- **Total Desktop apps**: 11 documented
- **Total Tools & Utilities**: 66+ tools

## Tools & Utilities MOC Updated

The main MOC has been reorganized and updated with:
- Better categorization
- All new tools added
- Improved sections for:
  - Terminals & Editors
  - Productivity & Automation
  - Development Tools
  - File & Directory Management
  - Development & Git
  - Package Managers & Environment

## Notable Tools Already Documented

### Previously Documented CLI Tools
- atuin, carapace, starship (in shell folder)
- bat, dust, fd
- git, lazygit, docker, colima
- tmux, zsh, nushell
- homebrew, mise, nix, uv
- yazi, zoxide
- And 30+ more...

### Previously Documented Desktop Apps
- Ghostty, VS Code, Obsidian
- Ice, Maccy, MenuWhere

## Installed But Not Documented

Some brew packages are dependencies or libraries and don't need individual documentation:
- System libraries (jpeg-turbo, libpng, etc.)
- Dependencies (openssl, curl, etc.)
- Fonts (installed as casks)
- Language-specific tools already covered

Some apps you have installed but not yet documented:
- 1Password, Arc, Slack, Vivaldi (browsers/common apps)
- iina, VLC (media players)
- Various fonts and utilities

## Benefits of This Sync

✅ **Comprehensive Documentation** - All your important CLI tools documented
✅ **Better Onboarding** - New team members can see what tools you use
✅ **Quick Reference** - Examples and usage for each tool
✅ **Tool Discovery** - Find tools you have installed but forgot about
✅ **Backup** - Documentation of your tooling choices

## Maintaining This Documentation

To keep it updated:

```bash
# Check for new packages
brew list --formula > /tmp/current-formulae.txt
brew list --cask > /tmp/current-casks.txt

# Compare with documented tools
ls -1 02-subjects/tools-and-utilities/cli/*.md | sed 's/.md$//'
ls -1 02-subjects/tools-and-utilities/desktop/*.md | sed 's/.md$//'
```

Or use the CLI tools we documented:

```bash
# See what's installed
brew list

# Search for a tool
brew search <name>

# Get info
brew info <name>
```

## Next Steps

Optional enhancements:
1. Add more desktop app documentation (Arc, Slack, etc.)
2. Create language-specific tool pages (Python, Node.js, etc.)
3. Add workflow examples combining multiple tools
4. Document your dotfiles/configurations
5. Create "tool stack" pages for specific tasks

---

**All tools documented with:**
- Installation instructions
- Common usage examples
- Key features
- Configuration tips
- Related tools
- Appropriate emojis! 🎨

**Back to:** [[00-INDEX|Main Index]] | [[tools-and-utilities|Tools & Utilities]]
