---
creation date: 2024-11-04 13:30
tags:
  - software/knowledge-base
description: Knowledge base
os:
  - linux
  - macos
  - windows
source: brew
url: https://obsidian.md
---
---
```cardlink
url: https://obsidian.md
title: "Obsidian - Sharpen your thinking"
description: "Obsidian is the private and flexible note‑taking app that adapts to the way you think."
host: obsidian.md
favicon: https://obsidian.md/favicon.ico
image: https://obsidian.md/images/banner.png
```

## to add property

Type `---` at the top of the file.

## paste without extra line

This is basically paste without style `Option + Cmd + Shift + V on Mac`.

## supported formats for internal links

Obsidian supports the following link formats:

- Wikilink: `[[Three laws of motion]]`
- Markdown: `[Three laws of motion](Three%20laws%20of%20motion.md)`

The examples above are equivalent—they appear the same way in the editor, and links to the same note.

Note

When using the Markdown format, make sure to [URL encode](https://en.wikipedia.org/wiki/Percent-encoding) the link destination. For example, blank spaces become `%20`.

By default, due to its more compact format, Obsidian generates links using the Wikilink format. If interoperability is important to you, you can disable Wikilinks and use Markdown links instead.

To use the Markdown format:

1. Open Settings.
2. Under Files & Links, disable Use [[Wikilink]].

Even if you disable the Wikilink format, you can still autocomplete links by typing two square brackets `[[`. When you select one of the suggested files, Obsidian instead generates a Markdown link.