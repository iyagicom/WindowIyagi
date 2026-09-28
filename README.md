# WindowIyagi

**See every open window and control it — on GNOME, KDE Plasma, Hyprland, sway or X11. From a window, or from your scripts.**

[English](README.md) · [한국어](README_ko.md)

## Why WindowIyagi?

- **Every window in one list.** Title, program, state and virtual desktop, with icons — updated live as windows open, close or change.
- **Control any of them.** Bring forward, minimize, maximize, restore or close. Close asks the program nicely, so unsaved work is never lost.
- **Works where other tools stop.** `wmctrl` and `xdotool` go blind on Wayland. WindowIyagi uses the right method for each desktop — GNOME, KDE Plasma, labwc, Wayfire, niri, Hyprland, sway and X11.
- **Scriptable.** `WindowIyagi --list` prints every window; `--activate`, `--minimize`, `--maximize`, `--restore`, `--close` take a window id. Great for shortcuts and automation.
- **Tells you why.** If something can't be seen or done on your desktop, a notice says so — and it reconnects by itself once fixed.

## Command line

```bash
WindowIyagi --list                  # print the window list
WindowIyagi --activate <window id>  # bring forward
WindowIyagi --minimize <window id>
WindowIyagi --maximize <window id>
WindowIyagi --restore  <window id>
WindowIyagi --close    <window id>
```

## Supported desktops

| Desktop | List | Activate | Minimize | Maximize · Restore | Close |
|---|---|---|---|---|---|
| GNOME | ✅ | ✅ | ✅ | ✅ | ✅ |
| KDE Plasma | ✅ | ✅ | ✅ | ✅ | ✅ |
| labwc · Wayfire · niri · Hyprland | ✅ | ✅ | ✅ | ✅ | ✅ |
| sway | ✅ | ✅ | — | — | ✅ |
| X11 (XFCE · MATE · Cinnamon · LXQt …) | ✅ | ✅ | ✅ | ✅ | ✅ |

On GNOME Wayland, the first run installs a small extension that passes the window list along — log out and back in once. (sway itself doesn't allow minimize/maximize.)

## Download

Packages for Ubuntu (deb), Fedora (rpm), Arch (pkg.tar.zst) and other distributions (AppImage, zip) will appear on the **[Releases](https://github.com/iyagicom/WindowIyagi/releases)** page.

WindowIyagi is also the window engine inside **[TaskIyagi](https://github.com/iyagicom/TaskIyagi)**, the taskbar for every Linux desktop.
