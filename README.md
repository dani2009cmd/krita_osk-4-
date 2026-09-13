# krita_osk-4-  # Krita One-Handed On-Screen Keyboard

A floating, semi-transparent bar of Krita shortcut buttons, built for one-handed
use. Dock it at the top or bottom of your screen, and click buttons with one
hand while your other hand stays on the mouse or tablet pen.

## Turning it into a standalone .exe (no AutoHotkey needed to run it)

If you'd rather not keep AutoHotkey installed just to run this, you can
compile it into a single `.exe` once:

1. Install AutoHotkey v2 (only needed for this one-time step).
2. Right-click `krita_osk.ahk` in File Explorer.
3. Choose **"Compile Script"** (this is added to the right-click menu by the
   AutoHotkey installer).
4. This creates `krita_osk.exe` in the same folder — a standalone program you
   can run (and share) without AutoHotkey installed at all.

If you ever want to change a shortcut or add a Custom button later, edit the
`.ahk` file and recompile — the `.exe` is just a frozen snapshot of it.

## Requirements

- Windows
- [AutoHotkey v2](https://www.autohotkey.com/) installed (the free "v2" version, not v1)

## Running it

1. Install AutoHotkey v2 if you haven't already.
2. Double-click `krita_osk.ahk`. The bar will appear docked at the bottom of
   your screen.
3. Click on your Krita canvas at least once so the script knows which window
   to send keystrokes to.
4. Click any button to send that shortcut to Krita.

## Layout

The bar has five tabs:

| Tab | What's in it |
|---|---|
| **Brush** | Brush/eraser toggle, brush size up/down, color darker/lighter, Pan mode toggle |
| **View / Canvas** | Zoom in/out, zoom 100%, fit to view, mirror canvas, rotate/reset rotation, canvas size dialog |
| **Layers** | Next/previous layer, merge down, new layer, toggle layer visibility |
| **Edit / Select** | Undo/redo, cut/copy/paste, clear, select all/deselect, transform |
| **Custom** | 8 blank buttons you can assign yourself |

## Pan Mode

Panning in Krita normally means holding Space while dragging with the mouse
— hard to do one-handed. The **Pan Mode** button toggles Space "held down" so
you can drag-pan with just your mouse hand. Click it again to release, or
press **F10** any time to force-release it if it ever gets stuck.

## Controls at the bottom of the window

- **Snap to Bottom / Snap to Top** — redocks the bar to the top or bottom of
  your screen.
- **Always on Top** — keeps the bar above other windows (on by default).
- **Opacity slider** — adjust how see-through the bar is.
- **Exit** — closes the script.

## Hotkeys

| Key | Action |
|---|---|
| **F9** | Show/hide the whole keyboard |
| **F10** | Force-release Pan mode (or any stuck held key) |

## Customizing the Custom tab

Right-click any button on the **Custom** tab to set:
- **Label** — what you see on the button
- **Key/shortcut** — using AutoHotkey's `Send` syntax, e.g.:
  - `^z` = Ctrl+Z
  - `^+z` = Ctrl+Shift+Z
  - `{F5}` = F5 key
  - `b` = the B key
  - `!{F4}` = Alt+F4

Left-click the button afterward to fire it. Your custom buttons are saved in
`krita_osk_settings.ini`, next to the script, so they persist between runs.

## If a shortcut doesn't match your Krita

Krita lets you remap shortcuts, and defaults have shifted slightly across
versions. If a button doesn't do what its label says, check **Settings →
Configure Krita → Keyboard Shortcuts** in Krita itself to see what's actually
bound, then either:
- edit the corresponding line in `krita_osk.ahk` (each button is created with
  a line like `AddBtn(MyGui, x, y, w, "Label", "key")` — just change the key
  string), or
- leave it and set up the equivalent on a **Custom** tab button instead.

## Troubleshooting

- **"No target window detected"** — click once on your Krita canvas, then try
  the button again.
- **Krita doesn't seem to receive the keystroke** — make sure Krita is the
  last window you clicked into (not some other app), and that it's not
  minimized.
- **Buttons look cut off or the bar appears in the wrong place** — this can
  happen on displays with Windows scaling other than 100%. The script sets
  itself as DPI-aware to avoid this; if it still looks off, let me know your
  display's scale percentage (Settings → Display → Scale) and whether you
  have multiple monitors.
