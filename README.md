# awes
anki wlroots extractor script(awes): Update anki cards with desktop audio, screenshots, and clipboard sentences on GNU/linux

Awes automates the process of adding information and media to your latest added Anki card; making immersion mining smoother and more efficient.

## Requirements
+ A bash interpreter
+ Anki and [AnkiConnect](https://ankiweb.net/shared/info/2055492159). *Note that Anki must be running*.
+ wlroots (GNOME doesn't support the screenshot protocol grim/slurp uses)
+ `pulseaudio` and `pactl`: detecting and recording from audio monitors
+ `ffmpeg`: encoding desktop audio
+ `grim`: screenshots
+ `slurp`: select a region
+ `libnotify`: sending notifications
+ `wl-clipboard`: pasting clipboard content

## Installation
### General
1. Download the awes.sh script somewhere safe
2. Edit the script and change the first two lines to match the names of your Anki model image and audio fields.
3. Bind the following commands to any key in your DE, WM, sxhkd, xbindkeysrc, etc.
    * `sh ~/path/to/awes.sh -r`: press once to start recording, and again to stop and export the audio clip to your latest-created Anki card.
    * `sh ~/path/to/awes.sh -s`: prompt for an interactive screenshot selection
    * `sh ~/path/to/awes.sh -a`: repeat the previous screenshot selection. If there is no previous selection, default to -s.
    * `sh ~/path/to/awes.sh -w`: screenshot the currently active window (requires xdotool)
    * `sh ~/path/to/awes.sh -c`: pastes the currently copied sentence in the clipboard (requires xsel)

## Notes
+ You may also define config options in `~/.config/awes/config`. These must be bash variable declarations, with no spaces like in the script.
+ awes tries to pick the right output monitor automatically. If this doesn't work for you, you can first list monitor sinks with `pactl list | grep -A2 '^Source #'` and then redefine the `OUTPUT_MONITOR` variable in the script or a config file with the name of the correct sink.
+ By default, images are scaled to a height of 300px
+ Prefix your awes command with `LANG=ja` for japanese notifications to achieve *maximum immersion*
