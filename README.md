# wintoggle

A bash cli that toggles a window in or out of the current active monitor.

## Dependencies
- `wmctrl`
- `xdotool`
- `pgrep`

## Install

Download script to machine where $PATH is available:

```bash
cd /tmp

desired_version=0.1.0

wget https://raw.githubusercontent.com/surgiie/wintoggle/refs/tags/v$desired_version/wintoggle

chmod u+x ./wintoggle
# example, update path as needed
mv ./wintoggle $HOME/.local/bin/wintoggle
```

## Usage:

```bash

# searches for a process with "firefox" in its name (the more characters here the better as its a "contains" search) and toggles it in or out of the current active monitor
wintoggle --name "firefox"

# when the application is not running, start it with the the same --name value, if the executabable differs from this value, use the --cmd flag, for example
# firefox is searchable in pgrep with "firefox-bin" but the executable is "firefox"
wintoggle --name "firefox-bin" --cmd "firefox"

```

**Note** The application window will be focused to the monitor where the mouse is.

### Hooks

If you'd like to execute some scripts or commands during you activate and minimize events, you can use the `--on-activate` and `--on-minimize` flags. For example, if you wanted
to play some sounds during these events, here's how you could go about it:

```bash
wintoggle --name "Firefox" --on-activate "ffplay -nodisp -autoexit $HOME/sounds/activate.mp3" --on-minimize "ffplay -nodisp -autoexit $HOME/sounds/minimize.mp3"
```
