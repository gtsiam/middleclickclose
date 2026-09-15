Quick Close in Overview
-----------------------
GNOME shell extension for quickly closing apps in the overview.

[![Download from extensions.gnome.org](img/ego.svg)](https://extensions.gnome.org/extension/352/middle-click-to-close-in-overview/)

## Features

- **Middle click to close**: Just hover over the app you want to close in the overview, and middle
  click. The mouse button that will trigger closing can be adjusted in the settings.
- **`Alt+F4` in the overview**: When triggering the close action (typically `Alt+F4`), the
  keyboard-focused window will be closed. This can be turned off in the settings. The keybind can be
  changed in Gnome Settings -> Keyboard -> Keyboard Shortcuts -> Close Window shortcut
- **Adjustable rearrange delay**: After closing an application, GNOME will wait a bit before
  rearranging the remaining windows. This extension allows configuring that delay.

## Building

Make sure the `gnome-extensions` executable is available on your `PATH` (It is typically bundled
with `gnome-shell`).

`make pack` will build a zip suitable for submission to [EGO](https://extensions.gnome.org/).

`make install` will install the extension for the current user.

`make install-system` will install the extension system-wide (By default, in /usr/local).

## Packaging

```bash
# Explicitly build extension package (optional)
make pack

# Install system-wide (by default, PREFIX=/usr/local)
make install-system PREFIX="$pkgdir/usr"
```

For a successful build, ensure these binaries are present:
- `gnome-extensions`
- `glib-compile-schemas`
- `unzip`

## Translations

If you're interested in contributing a translation, import the translation template under
`src/po/template.pot` to your favourite po-editing software and create a `*.po` file under `src/po`.

To update existing translations after changing the code, run `make po`.

## Debugging

- `journalctl -f --user` is your friend.
- For quick prototyping on wayland, use:
  - On Gnome >=49: `make install && dbus-run-session -- gnome-shell --devkit`.
  - On Gnome  <49: `make install && dbus-run-session -- gnome-shell --nested --wayland`.
- Running `dbus-run-session -- $SHELL` and then `make install && gnome-shell [..]` inside the
  spawned shell can make for a much faster debugging cycle.
- `make install`, then `Alt+F2`, `r` and `Enter` allow for quick prototyping under X11.
