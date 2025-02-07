# quake

A simple bash script to allow "quake" focus/hide on application windows while playing an mp3 sound at the same time with ffmpeg.

**Note** - This has not been tested other than personal use. If you notice issues, feel free to report/open a pull request.

## Dependencies
- `wmctrl`
- `xdotool`
- `pgrep`
- `ffmpeg/ffplay` (optional)

## Install

Download script to machine where $PATH is available:

```bash
cd /tmp

desired_version=0.1.0

wget https://raw.githubusercontent.com/surgiie/quake/refs/tags/v$desired_version/quake

chmod u+x ./quake

mv ./quake /usr/local/bin/quake
```

## Usage:

```bash
quake wezterm-gui /some/mp3file/to/play/on/focus /some/other/mp3file/to/play/on/hide
# OR if you dont want any sounds simply omit arguments
quake wezterm-gui
```

This script will look for a running process under the *EXACT* name of `wezterm-gui` using `pgrep -x -o wezterm-gui`  and then try to quake or start a new instance of it by calling a command with the same name, it is assumed the `$PATH` name is the same as the process name found by pgrep.

**Note** that this is not always the case. For example this is the case with google chrome. Google chrome will start under a process called "chrome" but the binary name to open the program from the terminal is usually called `google-chrome`, if thats the case you can specify this distinction by using this format:


```bash
quake chrome:google-chrome # Look for a process called "chrome" but use "google-chrome" when starting a new window when its not running.
```

**Note** The application window will be focused to the monitor where the mouse is.
