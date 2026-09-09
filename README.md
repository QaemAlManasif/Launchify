<div align="center">

<img src="Logo/launchify-icon-1024.png" alt="Launchify" width="110">

# Launchify

### Your apps, one tap away on the CORSAIR XENEON EDGE

[![Download](https://img.shields.io/badge/Download-Latest_release-ff6b35?style=for-the-badge)](../../releases/latest)
[![Setup Guide](https://img.shields.io/badge/Setup_Guide-2_minutes-2b2724?style=for-the-badge)](https://qaemalmanasif.github.io/Launchify/setup-guide.html)
[![Platform](https://img.shields.io/badge/Windows_10%2B-2b2724?style=for-the-badge)](#requirements)
[![iCUE](https://img.shields.io/badge/iCUE_5.45%2B-2b2724?style=for-the-badge)](#requirements)

</div>

---

<div align="center"><img src="assets/banner.png" alt="Launchify on the XENEON EDGE" width="900"></div>

---

**A launcher that knows what your PC is doing.** Every app you pin is a live tile: dim when it's closed, lit when it's running, hollow when it's minimized or sitting in the tray, and ringed when it's the window you're looking at right now.

Tap it to launch it. Tap it again to bring it forward. No alt-tabbing, no hunting through the taskbar, no Stream Deck required.

---

## 📥 Install

1. Download **`Launchify Helper Setup.exe`** and **`launchify.icuewidget`** from the [latest release](../../releases/latest).
2. Run the installer once. It puts a small background helper in `%LOCALAPPDATA%\Launchify`, starts it, and sets it to start with Windows.
3. In **iCUE → XENEON EDGE → Widgets**, import `launchify.icuewidget` and place it on a screen area.
4. Tap **+** and pin your first app.

No account, no keys, nothing to configure. Full walkthrough with screenshots: **[Setup Guide](https://qaemalmanasif.github.io/Launchify/setup-guide.html)**.

> Windows will show a **"Windows protected your PC"** screen the first time — the installer isn't code-signed. Click **More info → Run anyway**. The [Setup Guide](https://qaemalmanasif.github.io/Launchify/setup-guide.html) covers it.

---

## ✨ Key Features

<img src="assets/states.png" alt="Live app state" width="100%">

### 🟠 Live app tiles

| Feature | What it does |
| :-- | :-- |
| **Real state** | Closed, running, minimized, in the tray, or in front — read from the desktop's own windows several times a second. |
| **Window counts** | `Running · 3` for an app with three windows, and a `×2` chip when it's running more than once. |
| **Tray apps too** | Lightshot, Steam, a chat app you closed to the tray — no window to find, still shown as running. |
| **Real icons** | Extracted from the exe itself at up to 128px and cached, so your tiles look like your apps. |

### 👆 One tap does the obvious thing

| Feature | What it does |
| :-- | :-- |
| **Closed → launches it** | Straight from the exe, with your own command-line arguments if you set any. |
| **Running → brings it forward** | Restores it from minimized and puts it in front. |
| **In front → your call** | Minimize it (default), open another window, close it, or do nothing. |
| **Every gesture assignable** | A tap gets three bindings (closed / running / in front); double tap and long press get one each — launch, focus, new window, minimize, close, force close, next monitor, app menu, or nothing. |

### ⛔ Closing, with a confirm you can see

| Feature | What it does |
| :-- | :-- |
| **Two taps, clearly** | The app turns red, says **Close?**, and drains a bar for the couple of seconds it stays armed. |
| **Force close** | Task Manager's End task, for the app that stopped answering — its own confirm, its own colour. |
| **Both optional** | Turn either confirmation off if you'd rather they didn't ask. |

### 🖥️ Built for more than one monitor

<img src="assets/monitors.png" alt="Multi-monitor" width="100%">

| Feature | What it does |
| :-- | :-- |
| **Where everything is** | Each running app carries the number of the screen it's on, numbered the way Windows numbers them. |
| **Send it there** | Tap another number to move the app's windows — maximized windows are restored, moved and re-maximized on the new screen. |
| **Opens on** | Pin where an app should start. Windows gives no say in that, so the helper watches for the window and places it as it appears. |
| **Next monitor** | Also available as a gesture, so a double tap can walk an app across your screens. |

### ➕ Pin anything in two taps

<img src="assets/add.png" alt="Adding apps" width="100%">

| Source | What you get |
| :-- | :-- |
| **Running now** | Everything with a window this second. |
| **Installed** | Your whole Start Menu and Desktop, resolved to the real exe behind each shortcut. |
| **Browse…** | A real file picker, for anything else. |

The picker stays open as you add — each row marks itself **✓ Added**, with an **✕** to take it back off.

---

## 🎨 Customization

- **Grid or list** — app size from 60% to 180%, names and state lines on or off, and a filter for when the grid gets long.
- **Arrange mode** — `‹ › ✕` straight on every app, so reordering and removing take one tap each.
- **Badges, individually** — the status dot, the state line, the `×2` chip and the monitor number each have their own colour and their own switch. Leave a colour alone and it follows your accent.
- **Order** — your own order, running apps first, or by name.
- **Text size** — one overall dial plus separate ones for app names and for buttons and readouts.
- **Colours** — accent, background and transparency, or hand all of it to the screen's personalization with *Follow iCUE screen colours*.
- **Or skip the dialog** — every setting is also in iCUE's own widget settings panel, and the in-widget gear (or the whole header) can be hidden. Long-press the background for ~0.6s to get the dialog back.

---

## 📋 Requirements

| | |
| :-- | :-- |
| **Hardware** | CORSAIR XENEON EDGE (or any iCUE dashboard LCD) |
| **iCUE** | 5.45 or newer |
| **Operating system** | Windows 10 or later, 64-bit |
| **Account** | None. Launchify never talks to the internet. |
| **Stream Deck** | Not required. |

---

## 🧩 How it works

A widget page can't start a process, focus a window, read an exe's icon or list your Start Menu — so a small background helper does exactly those four things and nothing else.

```
Widget (XENEON EDGE)  ──ws 127.0.0.1:57131──▶  Launchify Helper  ──Win32──▶  your desktop
```

**Launchify Helper** has no window and no tray icon. It watches every top-level window on the desktop, mirrors "running / minimized / in the tray / focused / which monitor" to the widget, and carries out launch, focus, minimize, close, force close and move. When no widget is connected and iCUE isn't running, it idles down to a slow sweep.

| Path | |
| :-- | :-- |
| `%LOCALAPPDATA%\Launchify\LaunchifyHelper.exe` | The helper |
| `%LOCALAPPDATA%\Launchify\helper.log` | Log file |
| `%LOCALAPPDATA%\Launchify\icons` | Extracted icon cache |

Your pinned apps live in the widget's own storage, so uninstalling the helper doesn't lose them.

---

## 🩺 Troubleshooting

Most problems are one of these:

- **The widget says "Waiting for Launchify Helper…"** — the helper isn't running. Tap **Launch Launchify Helper** on that screen, or run the installer once.
- **An app shows as closed while it's running** — it was started from a different copy of the exe (a launcher that re-execs elsewhere). Re-pin it from **Running now**.
- **A window won't come forward** — some apps refuse focus while a full-screen game has it. Alt-tab out of the game first.
- **Moving to another monitor does nothing** — apps that manage their own window placement can snap straight back; there's no way around that from outside the app.

Full list with fixes: **[Setup Guide → If something doesn't work](https://qaemalmanasif.github.io/Launchify/setup-guide.html#troubleshooting)**

---

## 🔒 Privacy

Launchify makes no network requests of any kind. The helper listens on `127.0.0.1:57131` for the widget on the same PC, and that's the whole of it — no account, no telemetry, no cloud. Your pinned apps stay in the widget; the icon cache and log stay in `%LOCALAPPDATA%\Launchify`.

---

## 🗑️ Uninstall

**Settings → Apps → Launchify Helper**, or run `"Launchify Helper Setup.exe" /uninstall`. That removes the helper, its autostart entry, the `launchify://` scheme and the icon cache. Remove the widget from iCUE separately.

---

## 🛠️ Building from source

Needs the .NET 8 SDK. The installer embeds the published helper, so build the helper first:

```bash
cd "Launchify Widget/launchify-helper"
dotnet publish -c Release -o publish
cd setup && dotnet publish -c Release -o publish
```

Repackage the widget after editing anything under `launchify-widget/`:

```bash
cd "Launchify Widget"
python -c "import zipfile,os;z=zipfile.ZipFile('launchify.icuewidget','w',zipfile.ZIP_STORED);[z.write(os.path.join('launchify-widget',n),n) for n in ['index.html','manifest.json','resources/icon.svg','scripts/main.js','styles/main.css']];z.close()"
```

Marketing stills live in [`remotion/`](remotion) — `npm install && npm run thumbs`.

---

## 📄 License

MIT License. Designed and crafted for the XENEON EDGE by **QAEM**.
