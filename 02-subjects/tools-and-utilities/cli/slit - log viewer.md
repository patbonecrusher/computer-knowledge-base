---
creation date: 2024-12-15 21:57
tags:
  - dev/tools
  - shell/cli
description: Nice log viewer
os:
  - linux
  - macos
command: slit
source: brew
url: https://github.com/tigrawap/slit
---
---
```cardlink
url: https://github.com/tigrawap/slit
title: "GitHub - tigrawap/slit: slit - a modern PAGER for viewing logs, get more than most in less time"
description: "slit - a modern PAGER for viewing logs, get more than most in less time - tigrawap/slit"
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://opengraph.githubassets.com/dd82908130df103cb384c91245207a84f7131d54847007f29bf41ecd78119365/tigrawap/slit
```

```
go install github.com/tigrawap/slit/cmd/slit@latest
```

```
slit --filters="&StatTempApplication.cpp" -f tio_usb-FTDI_FT232R_USB_UART_AB841PGO-if00-port0_2024-12-09T22:17:11.log
```

## Search/Filters

- `/` - Forward search
- `?` - Backsearch
- `n` - Next match
- `N` - Previous match
- `CTRL + /` - Switch between `CaseSensitive` search and `RegEx`
- `&` - Filter: intersect
- `-` - Filter: exclude
- `+` - Filter: union
- ` =` - Remove all filters
- `U` - Removes last filter
- `C` - Stands for "Context", switches off/on all filters, helpful to get context of current line (which is the first line, at the top of the screen)

## Navigation

- `f`, `PageDown`, `Space`, `CTRL + F` - Page Down
- `CTRL + D` - Half page down
- `b`, `PageUp`, `CTRL + B` - Page Up
- `CTRL + U` - Half page up
- `g`, `Home` - Go to first line
- `G`, `End` - Go to last line
- `Arrow down`, `j` - Move one line down
- `Arrow up`, `k` - Move one line up
- `Arrow left`, `Arrow right` - Scroll horizontally
- `<`, `>` - Precise horizontal scrolling, 1 character a time

## Misc

- `K` - Keep N first characters(usually containing timestamp) when navigating horizontally  
    Up/Down arrows during K-mode will adjust N of kept chars
- `W` - Wrap/Unwrap lines
- `CTRL + S` - Save filtered version to file (will prompt for filepath)
- `q` - quit