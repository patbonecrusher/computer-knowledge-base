---
creation date: 2025-01-01 14:21
tags:
  - shell/cli
  - dev/language/go
  - dev/tools
command: goreleaser
description: 
os:
  - linux
  - macos
  - windows
source: brew
url: https://github.com/goreleaser/goreleaser
---
---
```cardlink
url: https://goreleaser.com/quick-start/
title: "GoReleaser - Quick Start"
description: "Release engineering, simplified."
host: goreleaser.com
favicon: ../static/favicon.ico
image: https://goreleaser.com//static/card.png
```


```shell
go install github.com/goreleaser/goreleaser/v2@latest

# cd in go repo
goreleaser init

# adjust created goreleaser config file.  for splistgo I had to enable cgo
vi .goreleaser.yaml

# update git repo
git add .goreleaser.yaml
git tag -a v0.0.3 -m "testing release"
git push origin v0.0.3

# to do a full release
goreleaser release

# to test
goreleaser release --snapshot --clean

# or try a local build only
goreleaser build --single-target

 
```

With this mechanism, I was able to then install my go app on a different computer using:
```shell
go install github.com/patbonecrusher/splistgo@v0.0.5

pat in 🌐 nostromo in ~
❯ splistgo
Port: /dev/cu.debug-console

Port: /dev/cu.Bluetooth-Incoming-Port

Port: /dev/cu.usbserial-212410
   USB ID      : 10C4:EA60
   USB serial  : 3037f6488a1ced1180a9c3b4bbdd3192

```