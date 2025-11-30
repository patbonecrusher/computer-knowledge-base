---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: rg
description: Ultra-fast grep alternative
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://github.com/BurntSushi/ripgrep
---

# 🔍 ripgrep (rg)

Extremely fast grep alternative that respects your gitignore.

## Features

- Recursively searches directories
- Respects .gitignore automatically
- Supports regex patterns
- Lightning fast (written in Rust)
- Smart case sensitivity
- Multi-threaded
- Supports many file encodings

## Installation

```bash
brew install ripgrep
```

## Common Usage

```bash
# Basic search
rg "pattern"

# Case insensitive
rg -i "pattern"

# Search specific file types
rg -t python "def"
rg -t rust "fn"

# Show files that would be searched
rg --files

# Search hidden files
rg --hidden "pattern"

# Don't respect .gitignore
rg --no-ignore "pattern"

# Show context (3 lines before and after)
rg -C 3 "pattern"

# Only show file names
rg -l "pattern"

# Search and replace (preview)
rg "old" -r "new"

# Count matches
rg "pattern" --count
```

## Advanced Examples

```bash
# Search only JavaScript and TypeScript
rg -t js -t ts "function"

# Exclude certain patterns
rg "TODO" -g "!node_modules/*"

# Search for whole words only
rg -w "word"

# Multiline search
rg -U "pattern.*spanning.*lines"

# Search in specific files
rg "pattern" -g "*.md"

# Use regex
rg "function \w+\("

# Search binary files
rg --text "pattern"

# List all file types
rg --type-list
```

## Integration

```bash
# With fzf for interactive search
rg --files | fzf

# With bat for preview
rg --json "pattern" | bat

# With vim
:grep pattern | copen  # if rg is set as grepprg
```

## Configuration

Create `~/.ripgreprc`:

```bash
# Always use smart case
--smart-case

# Show line numbers
--line-number

# Don't search these
--glob=!node_modules/*
--glob=!.git/*
--glob=!dist/*
--glob=!build/*
```

Set environment variable:
```bash
export RIPGREP_CONFIG_PATH="$HOME/.ripgreprc"
```

## Why ripgrep over grep?

- 10-100x faster for code searches
- Respects .gitignore by default
- Better defaults
- Parallel execution
- Better regex support

## Related

- [[02-subjects/tools-and-utilities/cli/the silver searcher|The Silver Searcher (ag)]] - Another fast grep alternative
- [[fzf|fzf]] - Fuzzy finder (works great with rg)
- [[02-subjects/tools-and-utilities/cli/fd|fd]] - Fast find alternative

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
