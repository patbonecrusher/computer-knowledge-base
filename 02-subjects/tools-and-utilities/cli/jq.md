---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: jq
description: JSON processor for command line
os:
  - linux
  - macos
source: Homebrew
url: https://jqlang.github.io/jq/
---

# 🔧 jq

Command-line JSON processor - like sed for JSON data.

## Features

- Parse and query JSON
- Transform JSON structures
- Filter and map data
- Format and pretty-print JSON
- Powerful query language

## Installation

```bash
brew install jq
```

## Common Usage

```bash
# Pretty print JSON
echo '{"name":"John","age":30}' | jq '.'

# Extract a field
echo '{"name":"John","age":30}' | jq '.name'

# Filter array
echo '[{"name":"John","age":30},{"name":"Jane","age":25}]' | jq '.[] | select(.age > 26)'

# Map over array
echo '[1,2,3]' | jq 'map(. * 2)'

# Get keys
echo '{"a":1,"b":2}' | jq 'keys'

# Combine queries
curl -s https://api.github.com/users/github | jq '.name, .location'
```

## Real-World Examples

```bash
# Parse package.json dependencies
jq '.dependencies' package.json

# Get AWS EC2 instance IDs
aws ec2 describe-instances | jq '.Reservations[].Instances[].InstanceId'

# Extract Docker container names
docker ps --format json | jq -r '.Names'

# GitHub API - get repo stars
gh api repos/owner/repo | jq '.stargazers_count'

# Transform JSON structure
jq '{fullName: (.firstName + " " + .lastName), age}' data.json

# Group by field
jq 'group_by(.category) | map({category: .[0].category, items: map(.name)})'
```

## Advanced Features

```bash
# Conditional logic
jq 'if .age > 18 then "adult" else "minor" end'

# Variables
jq --arg name "John" '.[] | select(.name == $name)'

# Multiple filters
jq '.[] | {name, email} | select(.email != null)'

# Raw output (no quotes)
jq -r '.name'

# Compact output
jq -c '.'

# Read from file
jq '.field' data.json

# Edit in place
jq '.version = "2.0"' package.json > temp.json && mv temp.json package.json
```

## Related

- [[yq|yq]] - YAML processor (similar to jq)
- [[curl|curl]] - HTTP client (often used with jq)

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
