---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: tree
description: Display directory tree structure
os:
  - linux
  - macos
source: Homebrew
url: http://mama.indstate.edu/users/ice/tree/
---

# 🌳 tree

Display directories as a tree structure - visualize folder hierarchies.

## Features

- Recursive directory listing
- ASCII tree visualization
- Filter by pattern
- Show file sizes
- Show permissions
- Colorized output
- JSON/XML/HTML output formats

## Installation

```bash
brew install tree
```

## Common Usage

```bash
# Basic tree
tree

# Limit depth
tree -L 2

# Show hidden files
tree -a

# Directories only
tree -d

# Show file sizes
tree -h

# Pattern matching
tree -P "*.md"

# Exclude pattern
tree -I "node_modules|dist|.git"

# Show full paths
tree -f

# Sort by modification time
tree -t

# JSON output
tree -J

# Count files and directories
tree --du

# Limit filesize display
tree -h --du
```

## Practical Examples

```bash
# Project structure (2 levels, dirs only)
tree -L 2 -d

# All markdown files
tree -P "*.md"

# Ignore common build directories
tree -I "node_modules|dist|build|coverage|.git"

# Show sizes in human-readable format
tree -h -L 2

# Save to file
tree > structure.txt

# Show only directories with sizes
tree -d -h --du

# Colorized tree
tree -C

# Reverse sort order
tree -r
```

## Advanced Options

```bash
# Custom indentation
tree --charset ascii

# Show permissions
tree -p

# Show user/group
tree -u -g

# Show file type indicator
tree -F

# Prune empty directories
tree --prune

# No indentation lines
tree --noreport

# File count summary
tree -L 2 | tail -1
```

## With Other Tools

```bash
# Combine with less for paging
tree -L 3 | less

# Find large directories
tree -h --du -L 2 | grep G

# Copy tree structure
tree -dfi | xargs mkdir -p
```

## Common Aliases

```bash
alias t="tree -L 2 -C"
alias td="tree -d -L 2 -C"
alias tf="tree -L 3 -C -I 'node_modules|.git'"
```

## Related

- [[eza|eza]] - Modern ls with tree view built-in
- [[02-subjects/tools-and-utilities/cli/fd|fd]] - Fast find alternative
- [[02-subjects/tools-and-utilities/cli/dust|dust]] - Disk usage visualizer

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
