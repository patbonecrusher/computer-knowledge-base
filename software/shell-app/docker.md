---
creation date: 2025-08-02 12:12:12
tags:
  - shell/cli
command: docker
description: container software
os:
  - linux
  - macos
  - windows
source: brew
url:
---
---

## To enable docker without having to use sudo

```bash
sudo chown -R $(id -u):$(id -g) $HOME/.docker
```