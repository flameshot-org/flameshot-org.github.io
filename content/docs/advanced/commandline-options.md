+++
title = "Command Line Options"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T18:20:00+00:00
updated = 2021-05-01T18:20:00+00:00
draft = false
weight = 2
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "Flameshot commandline options."
toc = true
top = false
+++

## Usage

You can always use `--help` for all commands or subcommands of Flameshot.

```sh
#      ___ command
#     |
# ,---^---,
  flameshot --help
#           '--v--'
#              |
#              -- Argument


#      ___ command  ____ Argument
#     |            |
# ,---^---,     ,--^--,
  flameshot gui --help
#           'v'
#            |
#            -- Subcommand
```

Example commands:

- capture with GUI:

   ```sh
   flameshot gui
   ```

- capture with GUI with custom save path:

   ```sh
   flameshot gui --path ~/myStuff/captures
   ```

- open GUI with a delay of 2 seconds:

   ```sh
   flameshot gui --delay 2000
   ```

- fullscreen capture (asking savepath):

   ```sh
   flameshot full
   ```

- fullscreen capture with custom save path (no GUI) and delayed:

   ```sh
   flameshot full --path ~/myStuff/captures --delay 5000
   ```

- fullscreen capture with custom save path copying to clipboard:

   ```sh
   flameshot full --clipboard --path ~/myStuff/captures
   ```

In case of doubt choose the first or the second command as shortcut in your favorite desktop environment.

A systray icon will be in your system's panel while Flameshot is running.
Do a right click on the tray icon and you'll see some menu items to open the configuration window and the information window.
Check out the information window to see all the available shortcuts in the graphical capture mode.


### Final Actions

In Flameshot (version 11.0.0 or later) we now have the concept of "final actions". These are things you would like to do after you have done with annotating your screenshot. The final actions are:

- `--path <path>`: Where the screenshot should be stored (can be path to the folder or the file)
- `--clipboard`: Whether the screenshot should be copied to the clipboard
- `--raw`: Send the screenshot to stdout
- `--upload`: Upload the screenshot
- `--pin`: Pin the screenshot
- `--print-geometry`: Write the position and dimension of the screenshot to stdout

The benefit of having the concept of Final Actions is that you can use more than one of them at the same time. For instance you can pin, copy to clipboard, save to a file, and get the geometry of the screenshot using this:

```sh
flameshot gui --pin --clipboard --path "~/Pictures" --print-geometry
```

These Final Actions can be used with `--accept-on-select` to immediately capture the selected area immediately after the mouse release.

**Note** that when you provide one or more Final Actions, the
"Copy" <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/content-copy.svg" />,
"Save" <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/content-save.svg" />,
"Image Upload" <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/cloud-upload.svg" />,
and "Pin Tool" <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/pin.svg" /> buttons will be removed from the buttons in `flameshot gui` and instead you will see a "Accept" <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/accept.svg"></img> button.


## CLI configuration

You can use the graphical menu to configure Flameshot, but alternatively you can use your terminal or scripts to do so.

- open the configuration menu:

    ```sh
    flameshot config
    ```

- show the initial help message in the capture mode:

    ```sh
    flameshot config --showhelp true
    ```

- to check mistakes and issues in the configuration file:

    ```sh
    flameshot config --check
    ```

- for more information about the available options use the help flag:

    ```sh
    flameshot config --help
    ```

## Available CLI options based on `--help`

This would list the available subcommands:
```console
❯  flameshot --help
Usage: flameshot [flameshot-options] [subcommands]

Per default runs Flameshot in the background and adds a tray icon for configuration.

Options:
-h, --help     Displays this help
-v, --version  Displays version information

Subcommands:
gui            Start a manual capture in GUI mode.
screen         Capture a screenshot of the specified monitor.
full           Capture screenshot of all monitors at the same time.
launcher       Open the capture launcher.
config         Configure flameshot.
```

This would show the acceptable arguments for the `gui` sumcommand:
```consol
❯  flameshot gui --help
Usage: flameshot gui [gui-options]

Per default runs Flameshot in the background and adds a tray icon for configuration.

Options:
-p, --path <path>             Existing directory or new file to save to
-c, --clipboard               Save the capture to the clipboard
-d, --delay <milliseconds>    Delay time in milliseconds
--region <WxH+X+Y or string>  Screenshot region to select
--last-region                 Repeat screenshot with previously selected region
-r, --raw                     Print raw PNG capture
-g, --print-geometry          Print geometry of the selection in the format WxH+X+Y. Does nothing if raw is specified
-u, --upload                  Upload screenshot
--pin                         Pin the capture to the screen
-s, --accept-on-select        Accept capture as soon as a selection is made
-h, --help                    Displays this help
```

This would show the acceptable arguments for the `screen` sumcommand:
```console
❯  flameshot screen --help
Usage: flameshot screen [screen-options]

Per default runs Flameshot in the background and adds a tray icon for configuration.

Options:
-n, --number <Screen number>  Define the screen to capture (starting from 0),
default: screen containing the cursor
-c, --clipboard               Save the capture to the clipboard
-p, --path <path>             Existing directory or new file to save to
-d, --delay <milliseconds>    Delay time in milliseconds
--region <WxH+X+Y or string>  Screenshot region to select
-r, --raw                     Print raw PNG capture
-u, --upload                  Upload screenshot
--pin                         Pin the capture to the screen
-h, --help                    Displays this help

```

This would show the acceptable arguments for the `full` sumcommand:
```console
❯  flameshot full --help
Usage: flameshot full [full-options]

Per default runs Flameshot in the background and adds a tray icon for configuration.

Options:
-p, --path <path>             Existing directory or new file to save to
-c, --clipboard               Save the capture to the clipboard
-d, --delay <milliseconds>    Delay time in milliseconds
--region <WxH+X+Y or string>  Screenshot region to select
-r, --raw                     Print raw PNG capture
-u, --upload                  Upload screenshot
-h, --help                    Displays this help
```

This would show the acceptable arguments for the `launcher` sumcommand:
```console
❯  flameshot launcher --help
Usage: flameshot launcher [launcher-options]

Per default runs Flameshot in the background and adds a tray icon for configuration.

Options:
-h, --help  Displays this help
```

This would show the acceptable arguments for the `config` sumcommand:
```console
❯  flameshot config --help
Usage: flameshot config [config-options]

Per default runs Flameshot in the background and adds a tray icon for configuration.

Options:
-a, --autostart <bool>            Enable or disable run at startup
-n, --notifications <bool>        Enable or disable the notifications
-f, --filename <pattern>          Set the filename pattern
-t, --trayicon <bool>             Enable or disable the trayicon
-s, --showhelp <bool>             Show the help message in the capture mode
-m, --maincolor <color-code>      Define the main UI color
-k, --contrastcolor <color-code>  Define the contrast UI color
--check                           Check the configuration for errors
-h, --help                        Displays this help
```
