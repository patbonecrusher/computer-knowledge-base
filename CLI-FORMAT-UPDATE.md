---
creation date: 2025-11-29
tags:
  - documentation
  - format
  - cli-tools
---

# 🔄 CLI Documentation Format Update

**Date**: 2025-11-29
**Status**: Partially Complete (Examples Provided)

## What Changed

CLI tool documentation files are being updated to a new, more comprehensive format for consistency and usability.

## New Format Template

All CLI tool documentation now follows this structure:

```markdown
---
creation date: YYYY-MM-DD
tags:
  - shell/cli
  - dev/tools
command: tool-name
description: Brief description
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://github.com/...
---

# 🔧 Tool Name

One-line description of what the tool does.

## Features

- Feature 1
- Feature 2
- Feature 3

## Installation

```bash
brew install tool-name
```

## Common Usage

```bash
# Example 1
tool command

# Example 2
tool --flag argument
```

## Configuration

Config file location and examples.

## Advanced Usage

More complex examples and use cases.

## Integration

How it works with other tools.

## Tips

Helpful tips and tricks.

## Troubleshooting

Common issues and solutions.

## Related

- [[other-tool|Other Tool]] - Description
- [[related-tool|Related Tool]] - Description

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
```

## Files Updated (Examples)

### Completed (10 files)

1. **bat.md** ✅
   - Full features section
   - Configuration examples
   - Integration with fzf, git, man
   - Custom themes
   - Common aliases
   - Related tools

2. **lazygit.md** ✅
   - Comprehensive key bindings
   - Configuration examples
   - Custom commands
   - Workflow examples
   - Integration with delta and vim
   - Tips and troubleshooting

3. **zoxide.md** ✅
   - Setup for all shells
   - Usage examples
   - Advanced features
   - Configuration options
   - Comparison with alternatives
   - Shell integration examples

4. **docker.md** ✅
   - Comprehensive container operations
   - Dockerfile best practices
   - Docker Compose examples
   - Networking and volumes
   - Multi-stage builds
   - Integration with OrbStack
   - Security best practices

5. **git.md** ✅
   - Complete workflow examples
   - Worktree usage
   - Git bisect guide
   - Interactive rebase
   - Branch management
   - Integration with gh, delta, lazygit
   - Troubleshooting common issues

6. **tmux.md** ✅
   - Complete key binding reference
   - Session management
   - Configuration examples
   - Plugin system (TPM)
   - Custom layouts
   - Integration examples
   - Workflow scripts

7. **yazi.md** ✅
   - Key bindings and navigation
   - Configuration (yazi.toml, keymap.toml, theme.toml)
   - File previews
   - Custom openers
   - Plugin examples
   - Shell integration
   - Multi-tab workflows

8. **fd.md** ✅
   - Pattern matching
   - Execute commands on results
   - Advanced filters (time, size)
   - Comparison with find
   - Integration with fzf, ripgrep, bat
   - Practical examples

9. **homebrew.md** ✅
   - Formulae and casks
   - Brewfile for reproducible setups
   - Taps and services
   - Version management
   - Maintenance scripts
   - Troubleshooting guide

10. **nushell.md** ✅
    - Structured data pipelines
    - Configuration (config.nu, env.nu)
    - Custom commands
    - Vi mode setup
    - Escaping to system commands
    - Data transformation examples

## Files Still Using Old Format (32 files)

### High Priority (Completed! ✅)
All high-priority files have been updated!

### Medium Priority
- dust.md
- colima.md
- ncdu.md
- btm.md (bottom)
- glances.md
- zenith.md
- scc.md
- goreleaser.md

### Lower Priority
- asciiquarium.md
- chezmoi.md
- fnt.md
- hexyl.md
- kalker.md
- lima.md
- m-cli.md
- mise-en-place.md (already good content)
- navi.md
- netop.md
- netscanner.md
- nix.md
- nvim.md
- pet.md
- slit - log viewer.md
- superfile.md
- the silver searcher.md
- tio.md
- trash-cli.md
- uv.md
- wscat.md
- ykush.md
- zsh.md
- hub (github).md

## Benefits of New Format

✅ **Consistency** - All tools documented the same way
✅ **Comprehensive** - More examples and use cases
✅ **Navigable** - Clear sections make finding info easier
✅ **Discoverable** - Related tools section connects ecosystem
✅ **Practical** - Real-world examples and workflows
✅ **Troubleshooting** - Common issues documented

## Key Improvements

1. **Structured Sections**
   - Features
   - Installation
   - Common Usage
   - Configuration
   - Advanced Usage
   - Integration
   - Tips
   - Troubleshooting
   - Related

2. **Better Examples**
   - Real-world use cases
   - Configuration snippets
   - Integration examples
   - Workflow demonstrations

3. **Cross-Referencing**
   - Links to related tools
   - Integration examples
   - Tool ecosystem mapping

4. **Consistent Metadata**
   - Proper frontmatter
   - OS compatibility
   - Source information
   - Command reference

## Next Steps

### Option 1: Continue Updating All Files
Update all 39 remaining files to the new format (would take significant time).

### Option 2: Update On-Demand
Update files as you use them or as needed.

### Option 3: Prioritize Key Tools
Update only the most frequently used tools:
- docker, git, tmux, yazi, fd, homebrew, nushell

## Template for Quick Updates

If updating manually, follow this checklist:

- [ ] Add emoji to H1 heading
- [ ] Add one-line description after H1
- [ ] Organize into sections (Features, Installation, Usage, etc.)
- [ ] Add configuration examples
- [ ] Add practical use cases
- [ ] Add Related section with links
- [ ] Add "Back to" link at bottom
- [ ] Verify frontmatter is complete

## Current Stats

- **Total CLI tools**: 55
- **New format**: 23 (13 newly created + 10 updated)
- **Old format**: 32
- **Completion**: 42%

## Latest Update (2025-11-30)

Completed all **7 high-priority** CLI tools:
- ✅ docker.md - Comprehensive container operations guide
- ✅ git.md - Complete version control reference
- ✅ tmux.md - Terminal multiplexer with key bindings
- ✅ yazi.md - Modern file manager documentation
- ✅ fd.md - Fast find alternative guide
- ✅ homebrew.md - Package manager reference
- ✅ nushell.md - Modern shell with structured data

All high-priority files now have:
- Features section
- Installation instructions
- Common usage examples
- Configuration examples
- Advanced usage
- Integration with other tools
- Tips and troubleshooting
- Related tools links

## Examples to Reference

For best practices, see:
- `eza.md` - Simple tool, well documented
- `fzf.md` - Medium complexity, great examples
- `lazygit.md` - Complex tool, comprehensive guide
- `zoxide.md` - Great configuration examples
- `jq.md` - Excellent real-world examples
- `gh.md` - Good workflow documentation

---

**Note**: All new CLI tools created during Homebrew sync already use the new format.

**Back to:** [[00-INDEX|Main Index]] | [[tools-and-utilities|Tools & Utilities]]
