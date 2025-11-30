---
creation date: 2025-11-29
tags:
  - desktop/app
  - automation
  - macos
description: Automation tool for macOS using Lua
os:
  - macos
source: Homebrew
url: https://www.hammerspoon.org
---

# 🔨 Hammerspoon

Powerful automation tool for macOS - control your Mac with Lua scripts.

## Features

- Window management
- Hotkey binding
- Application launching
- Menu bar widgets
- System event monitoring
- Network detection
- USB device detection
- Clipboard management
- And much more...

## Installation

```bash
brew install --cask hammerspoon
```

## Configuration

Config file: `~/.hammerspoon/init.lua`

## Examples

### Window Management

```lua
-- Move window to left half
hs.hotkey.bind({"cmd", "alt"}, "Left", function()
  local win = hs.window.focusedWindow()
  local f = win:frame()
  local screen = win:screen()
  local max = screen:frame()

  f.x = max.x
  f.y = max.y
  f.w = max.w / 2
  f.h = max.h
  win:setFrame(f)
end)

-- Move window to right half
hs.hotkey.bind({"cmd", "alt"}, "Right", function()
  local win = hs.window.focusedWindow()
  local f = win:frame()
  local screen = win:screen()
  local max = screen:frame()

  f.x = max.x + (max.w / 2)
  f.y = max.y
  f.w = max.w / 2
  f.h = max.h
  win:setFrame(f)
end)

-- Maximize window
hs.hotkey.bind({"cmd", "alt"}, "F", function()
  local win = hs.window.focusedWindow()
  local f = win:frame()
  local screen = win:screen()
  local max = screen:frame()

  f.x = max.x
  f.y = max.y
  f.w = max.w
  f.h = max.h
  win:setFrame(f)
end)
```

### Application Launcher

```lua
-- Quick app switching
local appKeys = {
  c = "Google Chrome",
  v = "Visual Studio Code",
  t = "iTerm",
  s = "Slack",
  m = "Mail"
}

for key, app in pairs(appKeys) do
  hs.hotkey.bind({"cmd", "shift"}, key, function()
    hs.application.launchOrFocus(app)
  end)
end
```

### Auto-Reload Config

```lua
function reloadConfig(files)
  doReload = false
  for _,file in pairs(files) do
    if file:sub(-4) == ".lua" then
      doReload = true
    end
  end
  if doReload then
    hs.reload()
  end
end

myWatcher = hs.pathwatcher.new(os.getenv("HOME") .. "/.hammerspoon/", reloadConfig):start()
hs.alert.show("Config loaded")
```

### Clipboard History

```lua
local clipboardHistory = {}
local clipboardWatcher = hs.pasteboard.watcher.new(function()
  local contents = hs.pasteboard.getContents()
  if contents then
    table.insert(clipboardHistory, 1, contents)
    if #clipboardHistory > 50 then
      table.remove(clipboardHistory)
    end
  end
end)
clipboardWatcher:start()

-- Show clipboard history with Cmd+Shift+V
hs.hotkey.bind({"cmd", "shift"}, "V", function()
  local chooser = hs.chooser.new(function(choice)
    if choice then
      hs.pasteboard.setContents(choice.text)
      hs.eventtap.keyStroke({"cmd"}, "v")
    end
  end)

  local choices = {}
  for i, item in ipairs(clipboardHistory) do
    table.insert(choices, {
      text = item,
      subText = "Clipboard item " .. i
    })
  end

  chooser:choices(choices)
  chooser:show()
end)
```

### Caffeine (Prevent Sleep)

```lua
local caffeine = hs.menubar.new()

function setCaffeineDisplay(state)
  if state then
    caffeine:setTitle("☕️")
  else
    caffeine:setTitle("💤")
  end
end

function caffeineClicked()
  setCaffeineDisplay(hs.caffeinate.toggle("displayIdle"))
end

if caffeine then
  caffeine:setClickCallback(caffeineClicked)
  setCaffeineDisplay(hs.caffeinate.get("displayIdle"))
end
```

### Network Watcher

```lua
function ssidChangedCallback()
  local ssid = hs.wifi.currentNetwork()
  if ssid then
    hs.notify.new({
      title="Network Changed",
      informativeText="Connected to: " .. ssid
    }):send()

    -- Different behavior based on network
    if ssid == "HomeWiFi" then
      -- Do home-specific setup
      hs.execute("networksetup -setdnsservers Wi-Fi 192.168.1.1")
    elseif ssid == "OfficeWiFi" then
      -- Do office-specific setup
      hs.execute("networksetup -setdnsservers Wi-Fi 10.0.0.1")
    end
  end
end

wifiWatcher = hs.wifi.watcher.new(ssidChangedCallback)
wifiWatcher:start()
```

### USB Device Detection

```lua
function usbDeviceCallback(data)
  if data["productName"] == "My External Drive" then
    if data["eventType"] == "added" then
      hs.notify.new({
        title="USB Device",
        informativeText="External drive connected"
      }):send()
    elseif data["eventType"] == "removed" then
      hs.notify.new({
        title="USB Device",
        informativeText="External drive removed"
      }):send()
    end
  end
end

usbWatcher = hs.usb.watcher.new(usbDeviceCallback)
usbWatcher:start()
```

## Spoons

Reusable Hammerspoon modules:

```lua
-- Install Spoon
hs.loadSpoon("SpoonInstall")

-- Load window manager Spoon
spoon.SpoonInstall:andUse("MiroWindowsManager", {
  hotkeys = {
    up = {{"cmd", "alt", "ctrl"}, "Up"},
    down = {{"cmd", "alt", "ctrl"}, "Down"},
    left = {{"cmd", "alt", "ctrl"}, "Left"},
    right = {{"cmd", "alt", "ctrl"}, "Right"}
  }
})
```

## Common Use Cases

1. Window management
2. App launcher/switcher
3. Clipboard history
4. Automating repetitive tasks
5. Context-aware automation (network, USB, etc.)
6. Menu bar widgets
7. Keyboard remapping
8. System monitoring

## Documentation

```lua
-- Open Hammerspoon console
hs.console.hswindow():focus()

-- Reload config
hs.reload()

-- Test code in console
hs.alert.show("Hello")
```

## Related

- [[raycast|Raycast]] - Alternative launcher with window management
- [[keyboard-maestro]] - GUI-based automation
- [[bettertouchtool]] - Gesture and keyboard customization

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
