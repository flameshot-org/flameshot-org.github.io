+++
title = "Key Bindings"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 2
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'Keyboard shortcuts for Flameshot.'
toc = true
top = false
+++

## Local
These shortcuts are available in GUI mode, meaning for example when you have ran `flameshot gui` command. In other words, these are the shortcuts that work *inside* the Flameshot application:

|  Keys                                                                                         |  Description                                  |
|---                                                                                            |---                                            |
| <kbd>←</kbd>, <kbd>↓</kbd>, <kbd>↑</kbd>, <kbd>→</kbd>                                        | Move selection 1px                            |
| <kbd>Shift</kbd> + <kbd><kbd>←</kbd>, <kbd>↓</kbd>, <kbd>↑</kbd>, <kbd>→</kbd></kbd>          | Resize selection 1px                          |
| <kbd>Esc</kbd>                                                                                | Quit capture                                  |
| <kbd>Ctrl</kbd> + <kbd>C</kbd>                                                                | Copy to clipboard                             |
| <kbd>Ctrl</kbd> + <kbd>S</kbd>                                                                | Save selection as a file                      |
| <kbd>Ctrl</kbd> + <kbd>Z</kbd>                                                                | Undo the last modification                    |
| Right Click                                                                                   | Show color picker                             |
| Mouse Wheel (scroll)                                                                          | Change the tool's thickness                   |
| <kbd>Shift</kbd> + drag a handler of the selection area                                       | Mirror re-dimension in the opposite handler.  |

You can change these default keybindings and more by opening the configuration, either by right-clicking on the tray icon or by running `flameshot config`, and navigating to **Shortcuts** tab:

![Flameshot configuration window and Shortcuts tab](/media/configuration_window/flameshot_config_shortcuts.png)

--------------------------------------------------------------------------------

## Global Shortcuts for Operating Systems

### macOS

By default you can start taking a screenshot using <kbd>Shift</kbd>+<kbd>CMD</kbd>+<kbd>x</kbd>. To know all the shortcuts, right-click on the tray icon, select the Configurations and go to Shortcuts tab.

--------------------------------------------------------------------------------

### Windows

Typically in Windows installations the <kbd>Prnt Scr</kbd> should work out of the box.

--------------------------------------------------------------------------------

### Linux

If you want use Flameshot as a default screenshot utility, chances are you want to launch it using the <kbd>Prnt Scr</kbd> key. Flameshot doesn't yet offer a fully-automated option to do it, but you can configure your system to do so.

#### On KDE Plasma desktop
To make configuration easier, there's [a file](https://github.com/flameshot-org/flameshot/blob/master/docs/shortcuts-config/flameshot-shortcuts-kde.khotkeys) in the repository that more or less automates this process. This file will assign the following keys to the following actions by default:

|  Keys                                                           |  Description                                                                                |
|---                                                              |---                                                                                          |
| <kbd>Prt Sc</kbd>                                               | Start the Flameshot screenshot tool and take a screenshot                                   |
| <kbd>Ctrl</kbd> + <kbd>Prt Sc</kbd>                             | Wait for 3 seconds, then start the Flameshot screenshot tool and take a screenshot          |
| <kbd>Shift</kbd> + <kbd>Prt Sc</kbd>                            | Take a full-screen (all monitors) screenshot and save it                                    |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Prt Sc</kbd>          | Take a full-screen (all monitors) screenshot and copy it to the clipboard                   |

If you don't like the defaults, you can change them manually later.

Steps for using the configuration:

1. The configuration file configures shortcuts so that Flameshot automatically saves (without opening the save dialog) screenshots to _~/Pictures/Screenshots_ folder. Make sure you have that folder by running the following command:
    ```sh
    mkdir --parents ~/Pictures/Screenshots
    ```
   (If you don't like the default location, you can skip this step and configure your preferred directory later.)

2. Download the configuration file:
    ```sh
    cd ~/Desktop
    wget https://raw.githubusercontent.com/flameshot-org/flameshot/master/docs/shortcuts-config/flameshot-shortcuts-kde.khotkeys
    ```
3. Go to _System Settings_ → _Shortcuts_ → _Custom Shortcuts_.
4. If there's one, you'll need to disable an entry for Spectacle, the default KDE screenshot utility first because its shortcuts might collide with Flameshot's ones; so, just uncheck the _Spectacle_ entry.
5. Click _Edit_ → _Import..._, navigate to the Desktop folder (or wherever you saved the configuration file) and open the configuration file.
6. Now the Flameshot entry should appear in the list. Click _Apply_ to apply the changes.
7. If you want to change the defaults, you can expand the entry, select the appropriate action and modify it as you wish; the process is pretty mush self-explanatory.

#### On Ubuntu and other Gnome based distros

You can easily configure your 'print' keyboard shortcut to be assigned to Flameshot. Below an example to open Flameshot in GUI mode:

1. Open _Settings_ → _Devices_ → _Keyboard_  → _Shortcuts_.

2. Search for 'print', and unbind the screen capture function by selecting it, and clicking _backspace_.

3. Scroll down and click on the '+'.

4. On 'Name', name it 'Flameshot' or 'PrintScreen'.

5. Define the command as 'flameshot gui'.

6. Select 'Define shortcut...'and click your keyboard <kbd>Prnt Scr</kbd> key.

Now you can use your default keyboard key to launch Flameshot.

For defining multiple shortcuts you can repeat the process above, and just change the command.

Some examples of commands are:

```sh
# Capture a region using the GUI, and have it automatically saved to your pictures folder when clicking the save button in GUI
flameshot gui --path /home/user/Pictures

# Capture the active monitor and save it automatically to your pictures folder
flameshot screen --path /home/user/Pictures

# Capture the full desktop (all monitors) and save it automatically to your pictures folder
flameshot full --path /home/user/Pictures

# Capture the region, copy to clipboard and at the same time write to file and pin the image
flameshot gui --clipboard --pin --path ~/Pictures
```
