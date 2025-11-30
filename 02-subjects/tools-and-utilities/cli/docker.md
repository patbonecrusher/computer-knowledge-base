---
creation date: 2025-08-02 12:12:12
tags:
  - shell/cli
  - dev/tools
  - containers
command: docker
description: Platform for developing, shipping, and running applications in containers
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://www.docker.com
---

# 🐳 Docker

Platform for developing, shipping, and running applications in containers - build once, run anywhere.

## Features

- Container runtime and orchestration
- Image management and registry
- Multi-platform support
- Networking and volumes
- Docker Compose for multi-container apps
- Layer caching for fast builds
- Dockerfile for reproducible builds
- Resource isolation and limits

## Installation

```bash
# Install Docker CLI (requires runtime like OrbStack or Docker Desktop)
brew install docker

# Install OrbStack (recommended - faster, lighter)
brew install --cask orbstack

# Or install Docker Desktop
brew install --cask docker
```

## Common Usage

```bash
# Run a container
docker run hello-world

# Run with interactive terminal
docker run -it ubuntu bash

# Run in background (detached)
docker run -d nginx

# Run with port mapping
docker run -p 8080:80 nginx

# Run with volume mount
docker run -v $(pwd):/app myimage

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container-id>

# Remove a container
docker rm <container-id>

# View container logs
docker logs <container-id>

# Follow logs in real-time
docker logs -f <container-id>

# Execute command in running container
docker exec -it <container-id> bash
```

## Image Management

```bash
# List images
docker images

# Pull an image from Docker Hub
docker pull nginx:latest

# Build image from Dockerfile
docker build -t myapp:latest .

# Tag an image
docker tag myapp:latest myapp:v1.0

# Push to registry
docker push myrepo/myapp:latest

# Remove an image
docker rmi <image-id>

# Remove unused images
docker image prune

# Remove all unused data (images, containers, volumes)
docker system prune -a
```

## Dockerfile Basics

```dockerfile
# Example Dockerfile
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy application code
COPY . .

# Expose port
EXPOSE 3000

# Set user (security best practice)
USER node

# Start command
CMD ["node", "server.js"]
```

## Docker Compose

```yaml
# docker-compose.yml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
    depends_on:
      - db
    volumes:
      - ./src:/app/src

  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: password
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

```bash
# Start services
docker-compose up

# Start in background
docker-compose up -d

# Stop services
docker-compose down

# Stop and remove volumes
docker-compose down -v

# View logs
docker-compose logs -f

# Rebuild and start
docker-compose up --build
```

## Networking

```bash
# List networks
docker network ls

# Create network
docker network create mynetwork

# Run container on network
docker run --network mynetwork nginx

# Inspect network
docker network inspect mynetwork

# Connect container to network
docker network connect mynetwork <container-id>
```

## Volumes

```bash
# List volumes
docker volume ls

# Create volume
docker volume create mydata

# Use volume
docker run -v mydata:/data myimage

# Inspect volume
docker volume inspect mydata

# Remove volume
docker volume rm mydata

# Remove unused volumes
docker volume prune
```

## Configuration

### Enable Docker Without Sudo (Linux)

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Fix permissions (if needed)
sudo chown -R $(id -u):$(id -g) $HOME/.docker

# Log out and back in for changes to take effect
```

### Docker Daemon Config

Location: `/etc/docker/daemon.json` (Linux) or Docker Desktop settings (macOS)

```json
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  },
  "default-address-pools": [
    {
      "base": "172.17.0.0/16",
      "size": 24
    }
  ]
}
```

## Advanced Usage

### Multi-stage Builds

```dockerfile
# Build stage
FROM node:18 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Production stage
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY package*.json ./
RUN npm ci --only=production
CMD ["node", "dist/server.js"]
```

### Health Checks

```dockerfile
HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget --quiet --tries=1 --spider http://localhost:3000/health || exit 1
```

```bash
# Check container health
docker inspect --format='{{.State.Health.Status}}' <container-id>
```

### Resource Limits

```bash
# Limit memory
docker run -m 512m nginx

# Limit CPU
docker run --cpus=1.5 nginx

# Limit CPU shares
docker run --cpu-shares=512 nginx
```

## Common Workflows

### Development Setup

```bash
# Start dev environment
docker-compose -f docker-compose.dev.yml up

# Run with live reload
docker run -v $(pwd):/app -p 3000:3000 myapp npm run dev
```

### Production Build

```bash
# Build production image
docker build -t myapp:prod --target production .

# Test locally
docker run -p 80:80 myapp:prod

# Tag and push
docker tag myapp:prod registry.com/myapp:1.0
docker push registry.com/myapp:1.0
```

## Integration

### With OrbStack

```bash
# OrbStack provides drop-in Docker compatibility
# Just use docker commands normally
docker run nginx

# Containers get automatic .local domains
docker run --name myapp nginx
# Access at http://myapp.local
```

### With VS Code

Install "Dev Containers" extension:
- Develop inside containers
- Consistent development environment
- Full IDE features

### With CI/CD

```yaml
# GitHub Actions example
- name: Build Docker image
  run: docker build -t myapp .

- name: Run tests
  run: docker run myapp npm test
```

## Useful Aliases

```bash
# Quick cleanup
alias dclean='docker system prune -af'

# Stop all containers
alias dstop='docker stop $(docker ps -aq)'

# Remove all containers
alias drm='docker rm $(docker ps -aq)'

# Docker compose shorthand
alias dc='docker-compose'
alias dcu='docker-compose up'
alias dcd='docker-compose down'

# View container IPs
alias dips='docker ps -q | xargs docker inspect --format "{{.Name}} {{.NetworkSettings.IPAddress}}"'
```

## Troubleshooting

```bash
# Check Docker daemon status
docker info

# View daemon logs (Linux)
sudo journalctl -u docker

# Debug network issues
docker network inspect bridge

# Check resource usage
docker stats

# Clean up disk space
docker system df
docker system prune -a --volumes

# Fix "Cannot connect to Docker daemon"
# Make sure Docker Desktop/OrbStack is running
# Or check docker service: sudo systemctl status docker
```

### Common Issues

**Port already in use:**
```bash
# Find process using port
lsof -i :8080

# Use different port
docker run -p 8081:80 nginx
```

**Image build fails:**
```bash
# Build without cache
docker build --no-cache -t myapp .

# Check Dockerfile syntax
docker build --check -t myapp .
```

**Container exits immediately:**
```bash
# Check logs
docker logs <container-id>

# Run with interactive shell to debug
docker run -it <image> sh
```

## Tips

- Use `.dockerignore` to exclude files from build context
- Multi-stage builds reduce image size significantly
- Always use specific image tags (not `:latest`) in production
- Use `docker-compose` for multi-container apps
- Clean up regularly with `docker system prune`
- Use OrbStack on macOS for better performance
- Leverage layer caching - put frequently changing commands last
- Use `COPY` instead of `ADD` unless you need extraction
- Don't run containers as root (use `USER` directive)

## Security Best Practices

```dockerfile
# Use specific versions
FROM node:18.17.0-alpine

# Don't run as root
USER node

# Use multi-stage to exclude build dependencies
FROM builder AS production

# Scan for vulnerabilities
# docker scout cves myapp:latest
```

## Related

- [[docker-compose|Docker Compose]] - Multi-container orchestration
- [[orbstack|OrbStack]] - Fast Docker runtime for macOS
- [[02-subjects/tools-and-utilities/cli/colima|Colima]] - Alternative Docker runtime
- [[kubernetes|Kubernetes]] - Container orchestration at scale
- [[podman|Podman]] - Daemonless container engine

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
