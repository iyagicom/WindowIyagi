# WindowIyagi

A window manager tool for the Linux desktop that lets you **see and control every open window at a glance**.

Whatever desktop you use, the same window shows the window list and lets you bring a window forward,
minimize, maximize, restore or close it. Command-line options are included, so scripts can work with
windows too.

WindowIyagi is also the engine that the IYAGI series taskbar **TaskIyagi** uses to handle windows.

[한국어](README.md)

---

## ✨ Features

### Window list
* **Every open window** — title · program · state · desktop (virtual desktop number, "all" when on every desktop)
* Shown with **program icons**
* **Active window marker** — the focused window is bold and marked with ●
* **Live updates** — windows opening, closing, or changing title or state show up immediately

### Window control
* **Activate** — bring the selected window forward (restoring it if minimized)
* **Minimize · Maximize · Restore** — Restore undoes one step at a time: minimized → fullscreen → maximized
* **Close** — sends the program a normal close request. If a document is unsaved, the program asks
  (nothing is force-killed)
* Actions your desktop does not support are greyed out; hover for the reason

### Status notices
* **Yellow strip** — when only part of the windows can be seen in this environment
* **Red strip** — when the window list is unavailable, with the reason
  (e.g. the GNOME extension is disabled · stopped with an error · the "User Extensions" switch is off)
* **Reconnects automatically** once the cause is resolved

### IYAGI series window
* Title-bar icon → About (version · licenses), name → Usage
* Resize from any edge; **Shift+drag** anywhere to move the window

---

## 🖥 Supported Desktops

WindowIyagi detects the desktop on start and picks the matching method, shown ("Environment · Backend") right below the title bar.

| Desktop | List | Activate | Minimize | Maximize · Restore | Close | Setup |
|---|---|---|---|---|---|---|
| **GNOME** (Ubuntu · Fedora default) | ✅ | ✅ | ✅ | ✅ | ✅ | **Log in again once** (see below) |
| **KDE Plasma** | ✅ | ✅ | ✅ | ✅ | ✅ | none (the package installs the KDE permission) |
| **labwc · Wayfire · niri · Hyprland** | ✅ | ✅ | ✅ | ✅ | ✅ | none |
| **sway** (tiling) | ✅ | ✅ | ❌ not accepted by sway | ❌ not accepted by sway | ✅ | none |
| **X11 sessions** (XFCE · MATE · Cinnamon · LXQt · GNOME/KDE on X11) | ✅ | ✅ | ✅ | ✅ | ✅ | none |

### First run on GNOME

For security, GNOME on Wayland does not show other programs' windows to ordinary apps — only GNOME Shell
itself can see them. So on first run WindowIyagi installs and enables a small **GNOME extension** that
passes the window list along.

1. Run WindowIyagi once — a notice above the list says "Installed the GNOME extension. It will start after you log in again"
2. **Log out and log back in** (GNOME loads new extensions only at login)
3. Run it again — every window is listed

* The extension only relays the window list and window control. It draws nothing on screen
* Turning off the **"User Extensions" main switch** in the Extensions app also turns this extension off.
  To turn off another extension, switch off just that one
* When a new version arrives, the extension is swapped in on launch (taking effect at the next login)

---

## 🎮 Usage

### The window

| To | Do |
|---|---|
| Bring a window forward | Select it and press **Activate**, or **double-click** it |
| Minimize · maximize · restore · close | Select the window and use the buttons below |
| See the result | The status bar shows "Done" or the reason for a few seconds |
| Usage · About | The name · icon in the title bar |
| Move the window | Drag the title bar, or **Shift+drag** |

### Command line

Print the window list as text, or control windows from scripts.

```bash
WindowIyagi --list                  # print the window list
WindowIyagi --activate <window id>  # bring forward
WindowIyagi --minimize <window id>
WindowIyagi --maximize <window id>
WindowIyagi --restore  <window id>
WindowIyagi --close    <window id>
```

Example `--list` output:

```
x11:0x1e00007      ----  desk=0   pid=9470    FileIyagi            FileIyagi
595917507          A---  desk=0   pid=10646   org.gnome.Ptyxis     Terminal
│                  │     │        │           │                    └ window title
│                  │     │        │           └ program
│                  │     │        └ process id (0 when unknown)
│                  │     └ virtual desktop (from 0, all = every desktop, -1 = unknown)
│                  └ A active · m minimized · M maximized · F fullscreen
└ window id — pass it to the other options as is
```

* On success a command prints `Done` and exits with 0; otherwise it prints the reason and exits with 1
* On **wlroots-based compositors** (labwc, sway …) window ids are numbered afresh on every run (`wlr:1`, `wlr:2` …).
  They follow the order windows were opened, so they usually match — if windows opened or closed in between,
  check `--list` again

### Other options

| Option · environment variable | Effect |
|---|---|
| `--install-extension` | Install the GNOME extension and exit (no window) |
| `--no-extension-sync` | Do not check or update the GNOME extension on launch |
| `WINDOWIYAGI_BACKEND=x11` · `gnome` · `kde` · `wlr` | Pick the method yourself instead of auto-detection (for troubleshooting) |
| `WINDOWIYAGI_DEBUG=1` | Log every window opening, closing and change to the terminal |

---

## 🔗 Relation to TaskIyagi

* **TaskIyagi** includes WindowIyagi's window engine. If you only use TaskIyagi, you do not need to install
  WindowIyagi separately
* Both share **the same GNOME extension** (`windowiyagi@iyagi.com`); whichever runs first installs it
* WindowIyagi also works as a check on what the taskbar sees — if TaskIyagi shows no window buttons, open
  WindowIyagi and look at the list and the reason in the red strip

---

## 🚀 Installation

### Ubuntu (deb)

```bash
sudo apt install ./windowiyagi_X.X.X~ubuntuXX.XX_amd64.deb
```

* Appears in the app list as **WindowIyagi**
* Qt and the other libraries it needs are bundled — nothing else to install
* On **GNOME**, log in again once after the first run ([why](#first-run-on-gnome))
* The file that grants KDE window-list permission is installed as well

### Removal

```bash
sudo apt remove windowiyagi
```

The GNOME extension stays in your user folder (`~/.local/share/gnome-shell/extensions/windowiyagi@iyagi.com`).
If you do not use TaskIyagi either, remove the WindowIyagi extension in the Extensions app.

---

## 👤 Developer

IYAGI INC
Email: [iyagicom@gmail.com](mailto:iyagicom@gmail.com)
GitHub: https://github.com/iyagicom

---

## 📜 License

Copyright (c) 2026 IYAGI INC. All rights reserved.

This software is provided in executable form only; the source code is not published.

You may freely use, install, package and redistribute it for any purpose — personal, commercial,
educational, governmental or organizational.

* The GNOME extension (`windowiyagi@iyagi.com`) is GPL-2.0-or-later
* License notices for the bundled open-source components (Qt, etc.) are in `/usr/share/doc/windowiyagi/licenses/`
