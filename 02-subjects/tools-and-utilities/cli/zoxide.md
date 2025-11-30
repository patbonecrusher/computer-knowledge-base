---
creation date: 2024-11-04 22:04
tags:
  - shell/cli
  - dev/tools
  - navigation
command: z
description: A smarter cd command that learns your habits
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://github.com/ajeetdsouza/zoxide
---

# 🚀 zoxide

A smarter `cd` command - supports all major shells and learns from your habits.

## Features

- Learns your most-used directories
- Fuzzy matching
- Interactive selection with fzf
- Much faster than alternatives
- Works with all major shells
- Importers from z, autojump, fasd
- Minimal configuration needed

## Installation

```bash
brew install zoxide
```

## Setup

### Zsh
```bash
# Add to ~/.zshrc
eval "$(zoxide init zsh)"
```

### Bash
```bash
# Add to ~/.bashrc
eval "$(zoxide init bash)"
```

### Fish
```bash
# Add to ~/.config/fish/config.fish
zoxide init fish | source
```

### Nushell
```bash
# Create ~/.zoxide.nu
zoxide init nushell | save -f ~/.zoxide.nu

# Add to config.nu
source ~/.zoxide.nu
```

## Usage

```bash
# Jump to a directory
z documents

# Jump to subdirectory
z doc/proj

# Jump using multiple keywords
z dev project

# Interactive selection (if multiple matches)
z proj
  # Shows list to choose from

# Go back to previous directory
z -

# List all tracked directories
zoxide query -l

# Show stats for a directory
zoxide query --score documents
```

## Advanced Usage

### Interactive Selection with fzf
```bash
# Use zi instead of z for interactive mode
zi proj

# This shows fzf interface with all matches
```

### Remove a directory
```bash
# Remove from database
zoxide remove /path/to/dir

# Remove current directory
zoxide remove .
```

### Import from other tools
```bash
# Import from z
zoxide import --from z path/to/z/data

# Import from autojump
zoxide import --from autojump path/to/autojump/data
```

## Configuration

### Custom Alias
```bash
# Use 'j' instead of 'z'
eval "$(zoxide init zsh --cmd j)"

# Now use
j documents
```

### Change fzf behavior
```bash
# Set FZF_DEFAULT_OPTS for interactive mode
export FZF_DEFAULT_OPTS="--height 40% --reverse"
```

## How It Works

1. Tracks directories you visit
2. Ranks them by "frecency" (frequency + recency)
3. Fuzzy matches your queries
4. Jumps to best match

### Algorithm
- More recent = higher score
- More frequent = higher score
- Older entries decay over time

## Comparison with Others

**vs z:**
- Faster
- Better matching algorithm
- Active development

**vs autojump:**
- Much faster
- Better shell support
- Simpler codebase

**vs fasd:**
- Still maintained
- Focused on directories only
- Better performance

## Tips

```bash
# Quick jump to projects
z proj

# Combine with other commands
cd $(zoxide query proj)

# Use partial matches
z dc/pr  # jumps to ~/Documents/Projects

# Multiple keywords
z my rust project  # jumps to ~/code/my-rust-project
```

## Shell Integration Examples

### Zsh with custom keybindings
```bash
# ~/.zshrc
eval "$(zoxide init zsh)"

# Ctrl-g to zi
bindkey -s '^g' 'zi\n'
```

### Fish abbreviations
```fish
# ~/.config/fish/config.fish
zoxide init fish | source
abbr --add zz 'z -'
abbr --add zl 'zoxide query -l'
```

## Troubleshooting

```bash
# Not finding directories?
# Check if they're in database
zoxide query -l | grep directory-name

# Add manually
zoxide add /path/to/directory

# View scores
zoxide query -l --score

# Clear all data (nuclear option)
rm -rf ~/.local/share/zoxide
```

## Related

- [[fzf|fzf]] - Fuzzy finder (used for interactive mode)
- [[eza|eza]] - Modern ls (often used together)
- [[cd|cd]] - Traditional directory change command

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
