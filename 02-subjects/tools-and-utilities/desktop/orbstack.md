---
creation date: 2025-11-29
tags:
  - desktop/app
  - docker
  - dev/tools
  - macos
description: Fast, light, and simple way to run Docker containers and Linux machines
os:
  - macos
source: Homebrew
url: https://orbstack.dev
---

# 🐳 OrbStack

The fast, light, and simple way to run Docker containers and Linux machines on macOS. A superior alternative to Docker Desktop.

## Features

- 10x faster than Docker Desktop
- Uses 50% less CPU and memory
- Instant startup
- Native macOS integration
- Linux machine management
- Rosetta support for x86 on Apple Silicon
- File sharing that actually works
- Free for personal use

## Installation

```bash
brew install --cask orbstack
```

## Key Advantages

### Performance
- Starts in <2 seconds
- Minimal resource usage
- Fast file sharing
- Native networking

### Simplicity
- No virtualization complexity
- Automatic updates
- Clean UI
- Just works™

### Integration
- Seamless Docker CLI compatibility
- Works with docker-compose
- Kubernetes support
- VS Code integration

## Usage

```bash
# Works exactly like Docker
docker run -it ubuntu

# Docker Compose
docker-compose up

# Access Docker daemon
docker ps

# List containers
orb list
```

## Linux Machines

Create and manage Linux VMs:

```bash
# Create a machine
orb create ubuntu

# Start a machine
orb start ubuntu

# SSH into machine
orb shell ubuntu

# Stop a machine
orb stop ubuntu

# Delete a machine
orb delete ubuntu
```

## File Sharing

```bash
# Volumes just work - no configuration
docker run -v $(pwd):/app myimage

# Access Linux machine files
# Automatically mounted at /Volumes/OrbStack
```

## Network

- Containers accessible from macOS
- Automatic DNS for containers
- No port forwarding needed
- localhost just works

```bash
# Container runs on port 8080
# Access at http://localhost:8080
# No -p mapping needed for local dev
```

## Domain Names

Containers get automatic .local domains:

```bash
docker run --name myapp nginx
# Access at http://myapp.local
```

## Kubernetes

```bash
# Enable Kubernetes
orb k8s start

# Use with kubectl
kubectl get pods
```

## Configuration

Settings UI:
- Resource limits
- Network settings
- Docker daemon config
- Linux machine templates

## CLI Commands

```bash
# Status
orb status

# Update
orb update

# Restart
orb restart

# View logs
orb logs

# Open UI
orb
```

## vs Docker Desktop

**Advantages:**
- Much faster (10x)
- Lower resource usage (50%)
- Instant startup
- Better file sharing
- Simpler
- Native macOS integration
- Free for personal use

**When to use Docker Desktop:**
- Enterprise license requirements
- Specific Docker Desktop extensions needed

## vs Colima

**Advantages over Colima:**
- GUI
- Easier setup
- Better performance
- Linux machine management
- Automatic updates
- File sharing easier

## Integrations

- Docker CLI
- Docker Compose
- Kubernetes
- VS Code Remote Containers
- IntelliJ/PyCharm Docker integration

## Common Workflows

### Web Development
```bash
# Run dev database
docker run -d -p 5432:5432 postgres

# Run app with volume mount
docker run -v $(pwd):/app myapp

# Access at http://localhost:3000
```

### Testing
```bash
# Run test containers
docker-compose -f docker-compose.test.yml up

# Clean up
docker-compose down -v
```

## Troubleshooting

```bash
# Restart daemon
orb restart

# Check status
orb status

# View logs
orb logs

# Reset (last resort)
orb reset
```

## Related

- [[04-archive/newvault/software/shell-app/docker|Docker]] - Container runtime
- [[04-archive/newvault/software/shell-app/colima|Colima]] - Alternative Docker runtime
- [[docker-compose|Docker Compose]] - Multi-container orchestration

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
