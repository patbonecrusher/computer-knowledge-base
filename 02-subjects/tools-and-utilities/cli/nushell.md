---
creation date: 2024-11-04 13:45
tags:
  - shell
  - shell/cli
  - dev/tools
command: nu
description: Modern shell with structured data support
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://www.nushell.sh
---

# 🐚 Nushell

A modern shell with structured data - pipelines for structured data, not just text.

## Features

- Structured data pipelines (JSON, CSV, YAML, etc.)
- Type system for data
- Rich data tables in output
- Built-in data manipulation commands
- Cross-platform (Linux, macOS, Windows)
- Plugin system
- Syntax highlighting
- Autocomplete
- Custom commands
- Vi/Emacs modes

## Installation

```bash
# macOS
brew install nushell

# Linux
cargo install nu

# Or download from https://github.com/nushell/nushell/releases
```

## Common Usage

### Basic Commands

```bash
# List files (returns structured data)
ls

# Filter by extension
ls | where type == file and name =~ ".md"

# Sort by size
ls | sort-by size

# Get top 5 largest files
ls | sort-by size | last 5

# Show as table
ls | table

# Convert to JSON
ls | to json

# Convert to CSV
ls | to csv
```

### Working with Structured Data

```bash
# Parse JSON
open data.json

# Query JSON
open data.json | get items

# Filter JSON
open data.json | where price > 100

# Parse CSV
open data.csv

# Query CSV
open data.csv | where age > 30 | select name age

# Parse YAML
open config.yml

# Parse TOML
open Cargo.toml
```

### Data Manipulation

```bash
# Select columns
ls | select name size

# Rename columns
ls | rename filename filesize

# Add calculated column
ls | insert megabytes { |row| $row.size / 1000000 }

# Group by
ls | group-by type

# Count items
ls | length

# Sum values
open sales.csv | get price | math sum

# Average
open sales.csv | get price | math avg

# Sort
ls | sort-by size --reverse
```

## Configuration

### Config Files

Nushell uses two main config files:
- `config.nu` - Main configuration
- `env.nu` - Environment variables

Location: `~/.config/nushell/` (macOS/Linux) or `%APPDATA%\nushell\` (Windows)

Find locations:
```bash
$nu.config-path    # Path to config.nu
$nu.env-path       # Path to env.nu
```

### Basic Configuration

Edit `~/.config/nushell/config.nu`:

```nu
# Editor
$env.EDITOR = "nvim"

# Vi mode
$env.config = {
    edit_mode: vi
    show_banner: false

    table: {
        mode: rounded
        index_mode: always
        trim: {
            methodology: wrapping
            wrapping_try_keep_words: true
        }
    }

    completions: {
        case_sensitive: false
        quick: true
        partial: true
    }

    history: {
        max_size: 10000
        sync_on_enter: true
        file_format: "sqlite"
    }

    filesize: {
        metric: false
        format: "auto"
    }
}
```

### Environment Variables

Edit `~/.config/nushell/env.nu`:

```nu
# Path
$env.PATH = ($env.PATH | split row (char esep) | prepend '/usr/local/bin')

# Colors
$env.LS_COLORS = (vivid generate molokai | str trim)

# Custom prompt
$env.PROMPT_COMMAND = {||
    let path_segment = ($env.PWD | str replace $nu.home-path "~")
    $"(ansi green)($path_segment)(ansi reset) > "
}

# Git prompt
$env.PROMPT_COMMAND_RIGHT = {||
    let git_branch = (do -i { git branch --show-current } | complete | get stdout | str trim)
    if ($git_branch | is-empty) {
        ""
    } else {
        $"(ansi yellow)($git_branch)(ansi reset)"
    }
}
```

## Custom Commands

Define in `~/.config/nushell/config.nu`:

```nu
# Simple command
def greet [name: string] {
    $"Hello, ($name)!"
}

# Command with optional parameters
def mkcd [path: string] {
    mkdir $path
    cd $path
}

# Command with flags
def search [
    pattern: string
    --case-sensitive (-c)
] {
    if $case_sensitive {
        rg $pattern
    } else {
        rg -i $pattern
    }
}

# Command with pipeline input
def get-largest [] {
    sort-by size | last
}

# Use: ls | get-largest
```

## Scripting

### Variables

```nu
# Immutable by default
let name = "value"

# Mutable
mut counter = 0
$counter = $counter + 1

# Environment variables
$env.MY_VAR = "value"
```

### Conditionals

```nu
# If statement
if $x > 10 {
    print "x is large"
} else if $x > 5 {
    print "x is medium"
} else {
    print "x is small"
}

# Match
match $value {
    0 => "zero",
    1..10 => "small",
    _ => "large"
}
```

### Loops

```nu
# For loop
for x in 1..10 {
    print $x
}

# Each (functional)
1..10 | each {|x| $x * 2 }

# While loop
mut i = 0
while $i < 10 {
    print $i
    $i = $i + 1
}
```

### Functions

```nu
# Define function
def double [x: int] -> int {
    $x * 2
}

# Function with pipeline
def sum-column [column: string] {
    get $column | math sum
}

# Use: open data.csv | sum-column price
```

## Escaping to System Commands

Nushell has built-in commands that may shadow system commands. Use `^` to escape:

```nu
# Nushell's built-in ls
ls

# System ls
^ls

# Nushell's built-in open (opens file in Nu)
open file.txt

# macOS open command (opens in default app)
^open file.txt

# Create alias for system command
alias sys-open = ^open

# Use alias
sys-open .  # Opens Finder on macOS
```

## Vi Mode

Enable vi mode in `$nu.config-path`:

```nu
$env.config = {
    edit_mode: vi
}

# Or temporarily
$env.config.edit_mode = "vi"
```

Vi keybindings:
- Normal mode: `Esc`
- Insert mode: `i`, `a`, `I`, `A`
- Delete: `dd`, `dw`, `x`
- Yank: `yy`, `yw`
- Paste: `p`, `P`
- Search: `/`, `?`
- Movement: `h`, `j`, `k`, `l`, `w`, `b`, `0`, `$`

## Advanced Usage

### Working with APIs

```nu
# HTTP GET
http get https://api.github.com/users/nushell

# POST with JSON
http post https://api.example.com/data { name: "test" }

# With headers
http get https://api.example.com/data --headers [Authorization "Bearer token"]
```

### File Operations

```nu
# Read file
open file.txt

# Write file
"content" | save file.txt

# Append to file
"more content" | save --append file.txt

# Copy files
cp source.txt dest.txt

# Move files
mv old.txt new.txt

# Remove files
rm file.txt

# Create directory
mkdir mydir

# Glob patterns
ls **/*.md
```

### Process Management

```nu
# List processes
ps

# Filter processes
ps | where name =~ "node"

# Kill process
ps | where name == "node" | each {|proc| kill $proc.pid }
```

### Data Transformation

```nu
# JSON to CSV
open data.json | to csv | save data.csv

# CSV to JSON
open data.csv | to json | save data.json

# Filter and transform
open data.json
| where status == "active"
| select id name price
| insert discount { |row| $row.price * 0.1 }
| to csv
| save discounts.csv
```

## Integration

### With Starship Prompt

In `env.nu`:

```nu
# Use Starship for prompt
$env.STARSHIP_SHELL = "nu"
def create_left_prompt [] {
    starship prompt --cmd-duration $env.CMD_DURATION_MS $'--status=($env.LAST_EXIT_CODE)'
}

$env.PROMPT_COMMAND = { create_left_prompt }
$env.PROMPT_COMMAND_RIGHT = ""
```

### With Zoxide

```nu
# In config.nu
# zoxide init nushell | save ~/.zoxide.nu
source ~/.zoxide.nu
```

### With Atuin

```nu
# History sync
atuin init nu | save ~/.atuin.nu
source ~/.atuin.nu
```

## Useful Aliases

```nu
# In config.nu

# Navigation
alias ll = ls -l
alias la = ls -a

# Git
alias gs = git status
alias ga = git add
alias gc = git commit

# Docker
alias d = docker
alias dc = docker-compose

# System commands
alias open = ^open  # Use system open on macOS
```

## Tips

- Nushell works with structured data, not just text
- Use `describe` to see the type of data: `ls | describe`
- Pipe to `table` for formatted output
- Use `help commands` to see all built-in commands
- Use `which` to see if command is built-in: `which ls`
- Tab completion works with data structures
- Use `^` prefix for system commands
- Enable vi mode for vim keybindings
- Use plugins for extended functionality
- Pipeline errors show the exact location

## Troubleshooting

### Command not found

```nu
# Check if it's a system command
which ls

# Use ^ to call system command
^ls

# Add to PATH in env.nu
$env.PATH = ($env.PATH | prepend '/new/path')
```

### Syntax errors

```nu
# Nushell is strict about types
# This fails: "5" + 5
# Do this instead:
"5" | into int | $in + 5

# Or
5 + ("5" | into int)
```

### Performance issues

```nu
# Nushell may be slower for large text processing
# Use system commands for large files
^grep pattern largefile.txt

# Or use streaming
open --raw largefile.txt | lines | where $it =~ "pattern"
```

## Comparison with Other Shells

### vs Bash/Zsh

**Pros:**
- Structured data handling
- Type safety
- Modern syntax
- Better error messages
- Cross-platform consistency

**Cons:**
- Different syntax (learning curve)
- Smaller ecosystem
- Some system integration quirks
- Slower for pure text processing

### vs PowerShell

**Pros:**
- Lighter and faster
- Better Unix integration
- More intuitive syntax
- Better cross-platform support

**Cons:**
- Smaller ecosystem
- Less enterprise tooling

## Related

- [[02-subjects/tools-and-utilities/cli/zsh|Zsh]] - Popular Unix shell
- [[bash|Bash]] - Traditional Unix shell
- [[02-subjects/tools-and-utilities/shell/starship|Starship]] - Cross-shell prompt
- [[02-subjects/tools-and-utilities/cli/zoxide|Zoxide]] - Smarter cd command
- [[atuin|Atuin]] - Shell history sync

---

**Resources:**
- [Nushell Book](https://www.nushell.sh/book/)
- [Command Reference](https://www.nushell.sh/commands/)
- [Awesome Nu](https://github.com/nushell/awesome-nu)

**Back to:** [[tools-and-utilities|Tools & Utilities]]
