# Arqen

**A floating Wayland desktop, written from scratch in C++20 on wlroots 0.20.**

Arqen looks like a modern desktop: light and dark themes tinted with an accent colour you choose, soft rounded cards, and the accent gradient on anything that's switched on. A few touches come from elsewhere: optional manga line art (bold window outlines, hard comic shadows) and the segmented LED gauge from Audi's cockpit displays, used in the on-screen display and the workspace pager.

![The Arqen desktop](screenshots/01-desktop.png)

> **Heads-up:** Arqen is written with an AI (Claude, by Anthropic). It's used every day, but it may have bugs. Keep another desktop (GNOME, KDE…) installed so you can always log in to that one.

---

## Contents

- [Screenshots](#screenshots)
- [Features](#features)
- [Install](#install)
- [Updating](#updating)
- [Uninstall](#uninstall)
- [Keyboard shortcuts](#keyboard-shortcuts)
- [Settings and the config file](#settings-and-the-config-file)
- [What it uses](#what-it-uses)
- [Building and hacking](#building-and-hacking)
- [License](#license)

---

## Screenshots

| | |
|---|---|
| ![App menu](screenshots/02-app-menu.png) **App menu**: pinned apps (drag them into order), connected devices, recent files, every app, and search across apps, files and settings. | ![Control centre](screenshots/03-control-centre.png) **Control centre**: a grid of tiles and sliders you can rearrange and resize. |
| ![Wi-Fi scanning](screenshots/04-wifi-scanning.png) **Wi-Fi and Bluetooth pages**: the Scan button and the sweeping line while it searches. | ![Overview](screenshots/05-overview.png) **Overview**: desktops and their windows (Super+Tab or Super+S). |
| ![Lock screen](screenshots/06-lock-screen.png) **Lock screen**: six styles, music controls, waiting-notification counts. | ![Settings](screenshots/07-settings.png) **Arqen Settings**: every option in one Qt app that follows your theme. |

![Lock screen styles in Settings](screenshots/08-settings-lock-styles.png)

---

## Features

### Look and feel
- **Light and dark themes**, with surfaces tinted by your **accent colour**. Choose a preset, pick any colour, or let the wallpaper choose one.
- **Accent gradients** on tiles, sliders, buttons that are on, and the main buttons in Settings.
- Optional **manga line art**: bold window outlines and hard comic-style shadows, or soft shadows, or none.
- Adjustable **roundness, transparency and blur** for panels, menus and cards.
- **Animations** you can tune: easing (smooth, snappy, bouncy), speed, or off.
- **Styles other apps**: GTK (GNOME), Qt (KDE) and Chrome-type browsers follow light/dark and your accent.
- A built-in **Arqen wallpaper** (a glowing ribboned gem in dark mode, lavender into rose in light mode), your own pictures, or a solid colour, with smooth transitions.
- **Wallpaper picker** on Super+W: arrow keys or scroll to choose, Enter to set.

### Panels and dock
- As many **panels** as you like, on any edge of any screen, as a bar or a **dock**, with **auto-hide**.
- Widgets you can arrange: app menu, pinned apps, task list, clock and calendar, media, tray, status, spacers, and an **LED workspace pager**.
- **Pinned apps** you can **drag into order**, running or not.
- Panels **disappear completely** when a fullscreen window is active on that desktop.
- **System tray** (StatusNotifierItem, plus old XEmbed icons).

### App menu
- Search **apps, files and folders, and Settings pages**, and do quick **sums**.
- **Pinned apps** in pages: right-click any app to pin it, drag pins to reorder.
- **Connected devices** (Bluetooth and KDE Connect) as battery rings.
- **Recent files**, and the full list of apps.

### Control centre
- A **customisable grid** (edit mode: move and resize tiles; each look keeps its own layout).
- Tiles for **Wi-Fi, Bluetooth, caffeine, night light, do not disturb, screenshot, airplane mode, dark mode**, and **power modes**.
- **Brightness, volume and microphone** sliders. The sound tiles open a **Sound** page with outputs, microphones, and each app's volume and output.
- **Wi-Fi and Bluetooth pages**: scan, connect (with a password field), pair. A sweeping accent line shows while it searches.
- **System monitor** (CPU, GPU, RAM) and **connected devices** with their batteries, including phones over **KDE Connect**.
- Right-click a tile, the media card or a notification and its options open **as a page of their own**.

### Notifications
- A full **notification server** with popups, a countdown bar, and a **notification centre** with history that's kept across restarts. Notifications can optionally be stacked by app.
- Click a notification to **open it downward** with simple options.
- **Reply inline** to KDE Connect messages, right in the notification.
- **Do not disturb**. You choose where popups appear (any of nine places) and how long they stay.

### Media and lyrics
- A **media card** that takes on the **album art's colours** (your accent if there's no art).
- **Synced lyrics** (from lrclib.net, or by listening with SongRec), plus a **beat visualiser**.
- Switch **audio output** from the media card.

### Lock screen
- Six **styles** (Classic, Stacked, Clock face, Corner, Outline, Minimal), with a live preview in Settings.
- **Music controls** along the bottom, **waiting notifications** (which apps and how many, never what they say), and Wi-Fi, sound and battery in the corner.
- Your picture and name, a show-password eye, a Caps Lock warning, and a sweeping line while your password is checked.
- Background: blurred wallpaper, your own picture, or a colour. Optional "just the clock" curtain.
- Locks on idle and before sleep. Unlocks through PAM.

### Windows and workspaces
- **Floating windows** with snapping: halves, maximise, and **snap layouts** (Super+Z).
- **Overview** with desktops and windows, and search.
- **Workspaces**: switch, move windows between them, hot corner.
- **Touchpad gestures**.
- **XWayland** for X11 apps, plus pointer lock for games and shortcut inhibiting.

### Tools
- **Screenshot tool** (Print): area, window or screen, with a pen to draw on it. It remembers the mode you used last.
- **Screen recording** (wf-recorder), with the recorded region outlined on screen.
- **Clipboard history** (Super+V).
- **Desktop icons**: files and folders on the desktop, and the Trash.
- **On-screen keyboard**.
- **Phone or tablet as a second screen** (virtual output over wayvnc).
- **System sounds**: pick a sound theme and turn individual sounds on or off.
- **Night light**, idle dim, screen off, lock and sleep, low-battery warnings.

### Arqen Settings
- One app for everything: Appearance, Panels & dock, Lock screen, Animations, Windows, Workspaces, Desktop & clipboard, Control centre, Notifications, On-screen display, Sounds, Displays, Keyboard, Mouse & touchpad, Power & battery, Default apps, Startup apps, Media & lyrics, Screenshots & recording, Date & time, Language & region, About.
- **Search** across all settings. Changes **apply instantly**.
- **Updates** from GitHub right inside Settings: steps, a progress bar, a colour console, and **Log out now** at the end.

---

## Install

Arqen is made on **Fedora** (44/45). Debian/Ubuntu and Arch are supported on a **best-effort, untested** basis.

```sh
git clone https://github.com/cache-byte/Arqen-de.git
cd Arqen-de
./build.sh install
```

`./build.sh` installs any missing packages (it asks for your password), downloads and builds [scenefx](https://github.com/wlrfx/scenefx) (rounded corners, shadows and blur), builds Arqen, and installs it as a login session.

Then **log out**, click the **gear** on the login screen, choose **Arqen**, and log in.

> If something goes wrong, **Ctrl+Alt+Backspace** quits Arqen and takes you back to the login screen.

### Try it first, in a window

```sh
./build.sh run
```

Arqen opens as a window inside your current desktop. Apps you launch from its menu open inside it. To start a terminal in it as well: `ARQEN_TERMINAL=kitty ./build.sh run`. (Night light and notifications only work when Arqen is your real session.)

### All build.sh commands

| Command | What it does |
|---|---|
| `./build.sh` | Install missing build packages, then build |
| `./build.sh run` | Build, then run Arqen in a window on your current desktop |
| `./build.sh install` | Build, then install Arqen as a login session |
| `./build.sh update` | Get the newest Arqen from GitHub and install it |
| `./build.sh uninstall` | Remove the installed session |
| `./build.sh fonts` | (Re)download Arqen's fonts |

Add `-y` (or `ARQEN_YES=1`) to skip the questions.

---

## Updating

- **From Settings:** *About → Updates → Check for updates → Update now*. Arqen is built on your computer (a few minutes). Your password is asked for once, and your settings stay as they are.
- **From a terminal:**

  ```sh
  arqen-update                # newest version from GitHub
  arqen-update --check        # just say what the newest version is
  arqen-update --downloads    # install the newest Arqen-*-source.zip in ~/Downloads
  arqen-update --zip FILE     # install from a zip you have
  ```

Log out and back in to start the new version.

---

## Uninstall

```sh
arqen-uninstall             # asks first
arqen-uninstall -y          # doesn't ask
arqen-uninstall --keep-themes
```

This removes Arqen and puts back what it changed for other desktops: GNOME appearance settings, GTK and Qt theming files, terminal fonts, cursor files, Flatpak permissions and the login screen entry. (`./build.sh uninstall` does the same from the source folder.)

---

## Keyboard shortcuts

| Keys | Action |
|---|---|
| Super (tap) or Alt+F1 | App menu |
| Super+A or Super+N | Control centre |
| Super+Tab or Super+S | Overview |
| Super+Enter | Terminal |
| Super+I | Arqen Settings |
| Super+E | Files |
| Super+L | Lock the screen |
| Super+V | Clipboard history |
| Super+W | Wallpaper picker |
| Super+D | Show the desktop (again to bring the windows back) |
| Print | Screenshot tool (area, window or screen) |
| Shift+Print / Alt+Print | Screenshot of all screens / the active window |
| Super+F | Fullscreen |
| Alt+Tab / Alt+Shift+Tab | Switch windows |
| Alt+F4 or Super+Q | Close window |
| Super+Up / Super+Down | Maximise / restore or minimise |
| Super+Left / Super+Right | Snap to the left or right half |
| Super+Z | Snap layouts for the active window |
| Super+Shift+Left / Right | Move the window to the next screen |
| Super + left-drag / right-drag | Move / resize a window from anywhere in it |
| Ctrl+Alt+Backspace | Quit Arqen |

Mouse: middle-click a window button on the panel to close the window, right-click a panel for its options, and right-click the wallpaper for the desktop menu.

---

## Settings and the config file

Open **Arqen Settings** from the gear in the app menu or the control centre, or with **Super+I**. Everything is saved in `~/.config/arqen/arqen.conf`, a plain `key = value` file you can also edit by hand. Arqen notices when it's saved.

```ini
theme = dark
accent = #9e1818
panels = main
panel.main.edge = bottom
panel.main.widgets = clock,tasks,spacer,overview,menu,spacer,media,tray,status
panel.main.pins = org.gnome.Nautilus.desktop,firefox.desktop
```

Screens are set by connector name (Settings → Displays shows it):

```ini
output.HDMI-A-1.mode = 2560x1440@143.912
output.HDMI-A-1.position = 1920,0
scale.eDP-1 = 1.25
primary_output = HDMI-A-1
```

Startup: `arqen -s "command"` runs a command once Arqen has started. `~/.config/arqen/autostart` runs at startup if it's executable. Apps in Settings → Startup apps (XDG autostart) start too.

---

## What it uses

All of these come with Fedora Workstation. If one is missing, its tile or slider just greys out.

| Tool | For |
|---|---|
| `nmcli` (NetworkManager) | Wi-Fi |
| `bluetoothctl` (BlueZ) | Bluetooth |
| `rfkill` | Airplane mode |
| `wpctl` (PipeWire / WirePlumber) | Volume and microphone |
| `brightnessctl` | Brightness |
| `powerprofilesctl` | Power modes |
| `systemd-inhibit` | Caffeine |
| `playerctl` | Media controls |
| `wf-recorder` | Screen recording |
| KDE Connect (optional) | Phone battery, messages and replies |
| wayvnc (optional) | Phone/tablet as a second screen |

---

## Building and hacking

Built with **meson** and **ninja**: C++20, wlroots 0.20, scenefx, cairo and pango for drawing, and Qt 6 for Settings.

```sh
./build.sh          # or: meson setup build && ninja -C build
./build/arqen -d    # verbose logging
```

| Where | What |
|---|---|
| `src/server.cpp` | Startup, screens, input, focus, shortcuts, night light |
| `src/view.cpp`, `src/xdg_view.cpp`, `src/xwayland.cpp` | Windows (Wayland and X11) |
| `src/panel.cpp` | Panels and their widgets |
| `src/launcher.cpp` | The app menu |
| `src/ccentre.cpp` | The control centre |
| `src/notify.cpp` | Notification server and popups |
| `src/lock.cpp` | The lock screen |
| `src/overview.cpp`, `src/workspaces.cpp` | Overview and workspaces |
| `src/system.cpp` | Network, sound, brightness, Bluetooth, battery, media |
| `src/ui.cpp`, `src/draw.cpp` | Shared drawing: cards, shadows, highlights, the busy bar, theme colours |
| `settings/main.cpp` | Arqen Settings (Qt 6) |
| `data/` | Session files, `arqen-update`, `arqen-uninstall`, `arqen-doctor`, theming scripts |

`arqen-doctor` checks dark mode, the keyring and polkit setup if something looks off. Crash logs go to `crash.log` and `arqen.log` in Arqen's state folder.

---

## License

[MIT](LICENSE)
