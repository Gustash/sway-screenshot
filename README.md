# sway-screenshot

[![AUR version](https://img.shields.io/aur/version/sway-screenshot?label=sway-screenshot&logo=arch+linux)](https://aur.archlinux.org/packages/sway-screenshot)
[![AUR git version](https://img.shields.io/aur/version/sway-screenshot-git?label=sway-screenshot-git&logo=arch+linux)](https://aur.archlinux.org/packages/sway-screenshot-git)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/Gustash/sway-screenshot?color=green&logo=github)](https://github.com/Gustash/sway-screenshot/releases/latest)

sway-screenshot is an utility to easily take screenshot in swaywm using your mouse.

It allows taking screenshots of windows, regions and monitors which are saved to a folder of your choosing and copied to your clipboard.

## Installation

### Arch Linux

You can install the [sway-screenshot](https://aur.archlinux.org/packages/sway-screenshot) package in AUR.

### Dependencies

- sway          (this one should be obvious)
- jq            (to parse and manipulate json)
- grim          (to take the screenshot)
- slurp         (to select what to screenshot)
- wl-clipboard  (to copy screenshot to clipboard)
- libnotify     (to get notified when a screenshot is saved)
- imagemagick   (to trim excess transparent pixels when window is partially off-screen)

### Manual

To install manually, simply clone this repo and copy/symlink the `sway-screenshot` script to a folder in your `PATH`:

```bash
$ git clone https://github.com/Gustash/sway-screenshot.git
$ ln -s $(pwd)/sway-screenshot/sway-screenshot $HOME/.local/bin
$ chmod +x sway-screenshot/sway-screenshot
```

## Usage

You can get help on how to use sway-screenshot by executing:

```bash
$ sway-screenshot -h
```

The simplest usage of sway-screenshot is executing it with one of the available modes.

For example, to screenshot an open window:

```bash
$ sway-screenshot -m window
```

You can also skip saving the screenshot to a file, copying it only to the clipboard:

```bash
$ sway-screenshot -m output --clipboard-only
```

## Configuration

You can add the various modes as keybindings in your Sway config like so:

```
# ~/.config/sway/config

...

# Screenshot a window
bindsym $mod+Print exec sway-screenshot -m window
# Screenshot a monitor
bindsym Print exec sway-screenshot -m output
# Screenshot a region
bindsym $mod+Shift+Print exec sway-screenshot -m region
```

This would allow you to:

Take a screenshot of a window by using `MOD + PrintScr`

Take a screenshot of a monitor by using `PrintScr`

Take a screenshot of a region by using `MOD + Shift + PrintScr`

## Save location

You can choose which directory sway-screenshot will save screenshots in by setting a `SWAY_SCREENSHOT_DIR` environment variable to your preferred location.

If `SWAY_SCREENSHOT_DIR` is not set, sway-screenshot will attempt to save to `XDG_PICTURES_DIR` and will further fallback to your home directory if this is also not available.
