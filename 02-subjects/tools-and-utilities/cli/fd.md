---
creation date: 2025-01-02 14:21
tags:
  - shell/cli
  - shell/replacements
  - dev/tools
command: fd
description: Fast and user-friendly alternative to find
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/sharkdp/fd
---

# 🔍 fd

Fast and user-friendly alternative to `find` - simple syntax, smart defaults, blazing speed.

## Features

- Intuitive syntax (no complex flags)
- Fast parallel directory traversal
- Respects `.gitignore` by default
- Colored output
- Smart case (case-insensitive by default, case-sensitive if uppercase)
- Regular expression patterns
- Parallel command execution
- Cross-platform (Linux, macOS, Windows)

## Installation

```bash
brew install fd
```

## Common Usage

```bash
# Find files by name (simple pattern)
fd pattern

# Find in specific directory
fd pattern /path/to/search

# Find files by extension
fd -e txt
fd -e md -e markdown

# Find directories only
fd -t d pattern

# Find files only
fd -t f pattern

# Find symlinks
fd -t l

# Find executable files
fd -t x

# Show hidden files
fd -H pattern

# Show ignored files (including .gitignore)
fd -I pattern

# Show both hidden and ignored
fd -HI pattern

# Case-sensitive search
fd -s pattern

# Case-insensitive search
fd -i pattern
```

## Search Patterns

```bash
# Simple substring match
fd config

# Regex pattern
fd '^test.*\.js$'

# Match exact name
fd -g 'README.md'

# Glob pattern
fd -g '*.json'
fd -g 'test-*.js'

# Multiple patterns
fd -e js -e ts

# Exclude patterns
fd -E node_modules -E .git pattern
```

## File Types

```bash
# -t flag specifies type:
# f = file
# d = directory
# l = symlink
# x = executable
# e = empty

# Find empty files
fd -t e

# Find empty directories
fd -t d -t e

# Find executable files
fd -t x

# Combine with patterns
fd -t f -e sh  # Shell scripts
```

## Advanced Usage

### Execute Commands

```bash
# Execute command on each result
fd pattern -x command {}

# Open all markdown files in vim
fd -e md -x nvim

# Delete all .tmp files
fd -e tmp -x rm

# Copy all .conf files
fd -e conf -x cp {} /backup/

# Execute with multiple placeholders
fd -e jpg -x convert {} {.}.png  # {.} = without extension

# Parallel execution (faster)
fd pattern -x command  # Uses all cores by default

# Limit parallel jobs
fd pattern -j 4 -x command
```

### With Other Tools

```bash
# Pipe to fzf
fd -t f | fzf

# With ripgrep
fd -e js -x rg 'pattern'

# With bat
fd -e py -x bat

# Count files
fd -t f | wc -l

# Size of all files
fd -t f -x du -sh {} | sort -h
```

### Advanced Filters

```bash
# Files modified in last 24 hours
fd --changed-within 24h

# Files modified more than 30 days ago
fd --changed-before 30d

# Files larger than 100MB
fd --size +100m

# Files smaller than 1KB
fd --size -1k

# Combine filters
fd -e log --changed-within 7d --size +10m

# Specific depth
fd --max-depth 2 pattern  # Search 2 levels deep
fd --min-depth 1 pattern  # Skip current directory
```

## Configuration

Config file: `~/.config/fd/ignore` or use `.fdignore` in any directory

```bash
# Global ignore patterns
echo "node_modules/" >> ~/.config/fd/ignore
echo "*.pyc" >> ~/.config/fd/ignore
echo ".DS_Store" >> ~/.config/fd/ignore
```

### Environment Variables

```bash
# In ~/.zshrc or ~/.bashrc

# Default command options
export FD_OPTIONS="--hidden --follow --exclude .git"

# Use with alias
alias fd='fd $FD_OPTIONS'
```

## Comparison with `find`

### find vs fd

**Find all JavaScript files:**
```bash
# find
find . -name '*.js'

# fd
fd -e js
```

**Find files modified today:**
```bash
# find
find . -type f -mtime 0

# fd
fd -t f --changed-within 1d
```

**Execute command on results:**
```bash
# find
find . -name '*.txt' -exec cat {} \;

# fd
fd -e txt -x cat
```

**Case-insensitive search:**
```bash
# find
find . -iname 'readme*'

# fd
fd -i readme
```

## Integration

### With FZF

```bash
# Use fd as fzf source
export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"

# Preview with bat
fd -t f | fzf --preview 'bat --color=always {}'
```

### With Vim/Neovim

```vim
" Use fd for file finding
if executable('fd')
  let $FZF_DEFAULT_COMMAND = 'fd --type f --hidden --follow --exclude .git'
endif
```

### With Zoxide

```bash
# Find and jump to directory
cd "$(fd -t d | fzf)"
```

### With Yazi

```bash
# Fd is already integrated in yazi
# Press 'F' in yazi to use fd for file finding
```

## Useful Aliases

```bash
# Find files by extension
alias fdf='fd -t f'
alias fdd='fd -t d'

# Search including hidden
alias fdh='fd -H'

# Search everything (hidden + ignored)
alias fda='fd -HI'

# Find and edit
alias fe='fd -t f | fzf | xargs nvim'

# Find recent files
alias fdr='fd --changed-within 1d'

# Find large files
alias fdl='fd -t f --size +10m'
```

## Common Patterns

### Development

```bash
# Find all test files
fd test

# Find configuration files
fd -g '*config*' -e json -e yaml -e toml

# Find source files
fd -e js -e ts -e jsx -e tsx

# Find all package.json files
fd -g 'package.json'

# Find files in src directory
fd -t f src/

# Exclude build and dependencies
fd -E node_modules -E dist -E build
```

### System Maintenance

```bash
# Find temporary files
fd -e tmp -e temp

# Find log files
fd -e log

# Find large files
fd -t f --size +100m

# Find empty directories
fd -t d -t e

# Find broken symlinks
fd -t l -x test -e {} \; -print
```

### Content Operations

```bash
# Count lines in all Python files
fd -e py -x wc -l | awk '{sum+=$1} END {print sum}'

# Search and replace in files
fd -e js -x sed -i '' 's/old/new/g'

# Copy all images to directory
fd -e jpg -e png -x cp {} /backup/images/

# Archive all logs
fd -e log -x tar -czf logs.tar.gz

# Convert all markdown to HTML
fd -e md -x pandoc {} -o {.}.html
```

## Tips

- `fd` is case-insensitive by default (smart case)
- Respects `.gitignore`, `.fdignore`, and global ignore
- Much faster than `find` for most use cases
- Colored output helps identify file types
- Use `-x` for executing commands (cleaner than `find -exec`)
- Combine with `fzf` for interactive file selection
- Use `--changed-within` for time-based searches
- `{}` placeholder in commands represents the file path
- `{.}` placeholder is the path without extension
- `{/}` is basename, `{//}` is parent directory

## Troubleshooting

### Not finding hidden files

```bash
# Use -H flag
fd -H pattern

# Or -HI for hidden + ignored
fd -HI pattern
```

### Too many results

```bash
# Limit depth
fd --max-depth 3 pattern

# Exclude directories
fd -E node_modules -E .git pattern

# Be more specific with pattern
fd '^exact-name$'
```

### Slow on large directories

```bash
# Limit depth
fd --max-depth 2

# Exclude large directories
fd -E target -E node_modules

# Use more specific patterns
```

## Advanced Examples

### Find and Archive

```bash
# Find and tar all config files
fd -e conf -e cfg | tar -czf configs.tar.gz -T -
```

### Find and Permissions

```bash
# Find and make executable
fd -e sh -x chmod +x

# Find world-writable files
fd -t f -x test -perm -002 {} \; -print
```

### Find and Git

```bash
# Find untracked files
fd -H -E .git --type f | while read f; do
  git ls-files --error-unmatch "$f" 2>/dev/null || echo "$f"
done
```

### Find and Process

```bash
# Find, sort by size, show top 10
fd -t f -x du -h | sort -rh | head -10

# Find and count by extension
fd -t f | sed 's/.*\.//' | sort | uniq -c | sort -rn
```

## Related

- [[ripgrep|ripgrep]] - Fast grep alternative (great with fd)
- [[fzf|fzf]] - Fuzzy finder (perfect combo with fd)
- [[02-subjects/tools-and-utilities/cli/bat|bat]] - Cat with syntax highlighting (for previewing fd results)
- [[eza|eza]] - Modern ls replacement
- [[02-subjects/tools-and-utilities/cli/yazi|yazi]] - File manager that integrates fd

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
