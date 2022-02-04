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
#     ___ command  ____ Argument
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
