---
creation date: 2024-11-04 13:30
tags:
  - dev/ide
  - software/ide
  - os/macos
  - os/linux
  - os/windows
description: IDE
os:
  - linux
  - macos
  - windows
source: brew
url: https://code.visualstudio.com
---
---
```cardlink
url: https://code.visualstudio.com
title: "Visual Studio Code - Code Editing. Redefined"
description: "Visual Studio Code redefines AI-powered coding with GitHub Copilot for building and debugging modern web and cloud applications. Visual Studio Code is free and available on your favorite platform - Linux, macOS, and Windows."
host: code.visualstudio.com
image: https://code.visualstudio.com/opengraphimg/opengraph-home.png
```

### references

```cardlink
url: https://www.youtube.com/watch?v=9_I0bySQoCs
title: "Transforming VS Code: Beyond Themes! — Make VS Code Unrecognizable!"
description: "In this video, we will explore how to customize VS Code beyond the usual options available through themes. We will significantly alter various aspects of the..."
host: www.youtube.com
favicon: https://www.youtube.com/s/desktop/97e0e051/img/logos/favicon_32x32.png
image: https://i.ytimg.com/vi/9_I0bySQoCs/maxresdefault.jpg
```

---
## file nesting

This enables hiding header files under source file.
![Screenshot 2024-11-07 at 10.01.11](attachments/Screenshot%202024-11-07%20at%2010.01.11.png)

```
  "explorer.fileNesting.enabled": true,
  "explorer.fileNesting.patterns": {
    "*.cts": "${capture}.typegen.ts",
    "*.js": "${capture}.js.map, ${capture}.min.js, ${capture}.d.ts",
    "*.jsx": "${capture}.js",
    "*.mts": "${capture}.typegen.ts",
    "*.ts": "${capture}.js, ${capture}.typegen.ts",
    "*.tsx": "${capture}.ts, ${capture}.typegen.ts",
    "*.c": "${capture}.h",
    "*.cpp": "${capture}.h",
    "package.json": "package-lock.json, yarn.lock, pnpm-lock.yaml",
    "tsconfig.json": "tsconfig.*.json"
  },
```

---
## hide submodules in git 

Add to `settings.json`

```json
{
    "git.detectSubmodulesLimit": 0,
    "git.detectSubmodules": false,
}
```

## shortcuts

### [Maximize Editor Group](https://code.visualstudio.com/updates/v1_84#_maximize-editor-group)

There is a new command **View: Toggle Maximize Editor Group** (⌘K ⌘M) to maximize an editor group. This will hide all other groups and adds a button to the tab bar, allowing the user to restore the previous layout. If the setting `workbench.editor.doubleClickTabToToggleEditorGroupSizes` is set to `maximize`, users can double-click on an editor tab to maximize and unmaximize the editor group.

### Toggle zen mode

(⌘K Z) 

## Config

### no title bar in zen mode
Add the following to `settings.json` to hide the title bar when in zen mode.
`"window.customTitleBarVisibility":"windowed",`

### hide breadcrumb bar

```
"breadcrumbs.enabled": false
```



---
## references

```cardlink
url: https://itnext.io/vs-code-shortcuts-to-code-like-youre-playing-a-piano-part-2-c27202ea7ea1
title: "VS Code Shortcuts to Code Like You’re Playing A Piano — Part 2"
description: "Significantly increase your focus and speed with these advanced vs code shortcuts"
host: itnext.io
favicon: https://miro.medium.com/v2/resize:fill:256:256/1*SiXeRxgOt0pAYlYhwZIu3g.png
image: https://miro.medium.com/v2/resize:fit:1200/0*EdYpKHW70AhoDKim.jpeg
```


```cardlink
url: https://code.visualstudio.com/docs/getstarted/userinterface
title: "Visual Studio Code User Interface"
description: "A quick overview of the Visual Studio Code user interface. Learn about the editor, window management, and special UI to handle source control, extension management, full text search and more."
host: code.visualstudio.com
image: https://code.visualstudio.com/opengraphimg/opengraph-docs.png
```



---
## extensions

### Project navigation/selection
#### Remote SSH
```cardlink
url: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh
title: "Remote - SSH - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Open any folder on a remote machine using SSH and take advantage of VS Code's full feature set."
host: marketplace.visualstudio.com
image: https://ms-vscode-remote.gallerycdn.vsassets.io/extensions/ms-vscode-remote/remote-ssh/0.116.2024110715/1730992722691/Microsoft.VisualStudio.Services.Icons.Default
```

#### Project dashboard
```cardlink
url: https://marketplace.visualstudio.com/items?itemName=kruemelkatze.vscode-dashboard
title: "Project Dashboard - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Organize your workspaces in a speed-dial manner."
host: marketplace.visualstudio.com
image: https://kruemelkatze.gallerycdn.vsassets.io/extensions/kruemelkatze/vscode-dashboard/2.6.0/1669153714791/Microsoft.VisualStudio.Services.Icons.Default
```


### Visual enhancement
#### Peacock
```cardlink
url: https://www.peacockcode.dev
title: "Peacock"
description: "Coloring your world, one Code editor at a time"
host: www.peacockcode.dev
```

#### Beatiful comment
```cardlink
url: https://marketplace.visualstudio.com/items?itemName=ParthR2031.colorful-comments
title: "Colorful Comments - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Improve and Enhance your code and make it attractive by adding Colorful Comments"
host: marketplace.visualstudio.com
image: https://parthr2031.gallerycdn.vsassets.io/extensions/parthr2031/colorful-comments/1.0.0/1658483004141/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=file-icons.file-icons
title: "file-icons - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - File-specific icons in VSCode for improved visual grepping."
host: marketplace.visualstudio.com
image: https://file-icons.gallerycdn.vsassets.io/extensions/file-icons/file-icons/1.1.0/1688483454970/Microsoft.VisualStudio.Services.Icons.Default
```




### Live preview code execution
#### ARepl for python
```cardlink
url: https://marketplace.visualstudio.com/items?itemName=almenon.arepl#overview
title: "AREPL for python - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - real-time python scratchpad"
host: marketplace.visualstudio.com
image: https://almenon.gallerycdn.vsassets.io/extensions/almenon/arepl/2.0.5/1678079316979/Microsoft.VisualStudio.Services.Icons.Default
```

#### Typescript worksheet
```cardlink
url: https://marketplace.visualstudio.com/items?itemName=chwoerz.ts-worksheet
title: "TypeScript Worksheet - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Live preview of your code right inside your editor"
host: marketplace.visualstudio.com
image: https://chwoerz.gallerycdn.vsassets.io/extensions/chwoerz/ts-worksheet/0.8.27/1729027053994/Microsoft.VisualStudio.Services.Icons.Default
```


### Language specifics
### Json crack
```cardlink
url: https://marketplace.visualstudio.com/items?itemName=AykutSarac.jsoncrack-vscode
title: "JSON Crack - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Seamlessly visualize your JSON data instantly into graphs."
host: marketplace.visualstudio.com
image: https://aykutsarac.gallerycdn.vsassets.io/extensions/aykutsarac/jsoncrack-vscode/2.0.3/1711383474427/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=cschlosser.doxdocgen
title: "Doxygen Documentation Generator - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Let me generate Doxygen documentation from your source code for you."
host: marketplace.visualstudio.com
image: https://cschlosser.gallerycdn.vsassets.io/extensions/cschlosser/doxdocgen/1.4.0/1645786891772/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig
title: "EditorConfig for VS Code - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - EditorConfig Support for Visual Studio Code"
host: marketplace.visualstudio.com
image: https://editorconfig.gallerycdn.vsassets.io/extensions/editorconfig/editorconfig/0.16.4/1607315835386/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens
title: "Error Lens - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Improve highlighting of errors, warnings and other language diagnostics."
host: marketplace.visualstudio.com
image: https://usernamehw.gallerycdn.vsassets.io/extensions/usernamehw/errorlens/3.20.0/1719044874383/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens
title: "GitLens — Git supercharged - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Supercharge Git within VS Code — Visualize code authorship at a glance via Git blame annotations and CodeLens, seamlessly navigate and explore Git repositories, gain valuable insights via rich visualizations and powerful comparison commands, and so much more"
host: marketplace.visualstudio.com
image: https://eamodio.gallerycdn.vsassets.io/extensions/eamodio/gitlens/2024.11.904/1731143307732/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid
title: "Markdown Preview Mermaid Support - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - Adds Mermaid diagram and flowchart support to VS Code's builtin markdown preview"
host: marketplace.visualstudio.com
image: https://bierner.gallerycdn.vsassets.io/extensions/bierner/markdown-mermaid/1.26.0/1729712560714/Microsoft.VisualStudio.Services.Icons.Default
```



```cardlink
url: https://marketplace.visualstudio.com/items?itemName=pnp.polacode
title: "Polacode - Visual Studio Marketplace"
description: "Extension for Visual Studio Code - 📸  Polaroid for your code"
host: marketplace.visualstudio.com
image: https://pnp.gallerycdn.vsassets.io/extensions/pnp/polacode/0.3.4/1569601471865/Microsoft.VisualStudio.Services.Icons.Default
```



---
## other extensions

```cardlink
url: https://blog.devgenius.io/best-vscode-extensions-im-in-love-with-%EF%B8%8F-e50981fa0767
title: "Best VSCode Extensions I’m in Love With! ❤️"
description: "Discover the best VSCode extensions that enhance your coding experience! From Console Ninja to VSCode Pets, check out my favorites that…"
host: blog.devgenius.io
favicon: https://miro.medium.com/v2/resize:fill:256:256/1*CvejhRq3NYsivxILYXEdfA.jpeg
image: https://miro.medium.com/v2/resize:fit:1200/1*xGN-hqNNL_V_P2gB6MrPhA.jpeg
```

