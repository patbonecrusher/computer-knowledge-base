---
creation date: 2025-01-03 14:55
tags:
  - shell/cli
  - dev/tools
  - git
command: lazygit
description: Simple terminal UI for git commands
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://github.com/jesseduffield/lazygit
---

# 🌿 lazygit

A simple terminal UI for git commands - making Git easier and more intuitive.

## Features

- Interactive staging/unstaging
- Branch management
- Commit history visualization
- Rebase interactive mode
- Stash management
- Cherry-pick
- Diff viewing
- Merge conflict resolution
- Custom commands
- Mouse support

## Installation

```bash
brew install lazygit
```

## Usage

```bash
# Start lazygit in current repo
lazygit

# Start in specific directory
lazygit -p /path/to/repo

# Show version
lazygit --version
```

## Key Bindings

### General
- `?` - Open help menu
- `x` - Open command menu
- `q` - Quit
- `Esc` - Cancel/Go back
- `PgUp/PgDn` - Scroll

### Files Panel
- `Space` - Stage/unstage file
- `a` - Stage/unstage all
- `d` - View delete options
- `c` - Commit changes
- `Enter` - View file diff

### Commits Panel
- `Enter` - View commit
- `c` - Checkout commit
- `d` - Delete commit
- `r` - Reword commit
- `R` - Rebase
- `s` - Squash commit
- `g` - Reset to commit

### Branches Panel
- `Space` - Checkout branch
- `n` - New branch
- `d` - Delete branch
- `r` - Rebase branch
- `M` - Merge branch
- `f` - Fast-forward branch

### Stash Panel
- `Space` - Apply stash
- `g` - Pop stash
- `d` - Drop stash

## Configuration

Config file: `~/.config/lazygit/config.yml`

```yaml
gui:
  theme:
    activeBorderColor:
      - green
      - bold
    inactiveBorderColor:
      - white

git:
  paging:
    colorArg: always
    pager: delta --dark --paging=never

customCommands:
  - key: 'P'
    command: 'git push --force-with-lease'
    context: 'global'
    description: 'Push (force with lease)'
```

## Custom Commands

Add to config.yml:

```yaml
customCommands:
  - key: 'C'
    command: 'git cz'
    context: 'files'
    description: 'Commit with Commitizen'

  - key: 'o'
    command: 'gh pr view --web'
    context: 'global'
    description: 'Open PR in browser'
```

## Workflow Examples

### Basic Commit Workflow
1. `lazygit` - Open lazygit
2. `Space` on files to stage
3. `c` - Commit
4. Type message
5. `Enter` - Confirm
6. `P` - Push

### Interactive Rebase
1. Navigate to Commits panel
2. `e` on commit to edit
3. `r` to reword
4. `s` to squash
5. `Enter` to continue

### Branch Operations
1. Navigate to Branches panel
2. `Space` to checkout
3. `M` to merge
4. `r` to rebase

### Conflict Resolution
1. Navigate to Files panel
2. `Enter` on conflicted file
3. `Space` to choose left/right
4. Or `e` to edit manually
5. `Esc` when done
6. `c` to commit

## Integration

### With delta
```yaml
# config.yml
git:
  paging:
    pager: delta --paging=never
```

### With vim
```yaml
# config.yml
os:
  editCommand: 'nvim'
  editCommandTemplate: '{{editor}} +{{line}} {{filename}}'
```

## Tips

- Use `x` menu for less common operations
- Use `?` to see all key bindings
- Mouse scroll and click work!
- `<c-r>` to refresh
- Customize key bindings in config
- Use custom commands for repetitive tasks

## Troubleshooting

```bash
# Clear cache
rm -rf ~/.local/state/lazygit/

# Check config
lazygit --use-config-file ~/.config/lazygit/config.yml --debug
```

## Related

- [[02-subjects/tools-and-utilities/cli/git|Git]] - Version control
- [[gh|gh]] - GitHub CLI
- [[git-delta|git-delta]] - Better diff viewer
- [[fzf|fzf]] - Fuzzy finder

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
