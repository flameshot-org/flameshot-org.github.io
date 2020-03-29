## Keyboard shortcuts

### Local
These shortcuts are available in GUI mode:

|  Keys                                                                                         |  Description                         |
|---                                                                                            |---                                   |
| <kbd>←</kbd>, <kbd>↓</kbd>, <kbd>↑</kbd>, <kbd>→</kbd>                                        | Move selection 1px                   |
| <kbd>Shift</kbd> + <kbd><kbd>←</kbd>, <kbd>↓</kbd>, <kbd>↑</kbd>, <kbd>→</kbd></kbd>          | Resize selection 1px                 |
| <kbd>Esc</kbd>                                                                                | Quit capture                         |
| <kbd>Ctrl</kbd> + <kbd>C</kbd>                                                                | Copy to clipboard                    |
| <kbd>Ctrl</kbd> + <kbd>S</kbd>                                                                | Save selection as a file             |
| <kbd>Ctrl</kbd> + <kbd>Z</kbd>                                                                | Undo the last modification           |
| Right Click                                                                                   | Show color picker                    |
| Mouse Wheel                                                                                   | Change the tool's thickness          |

<kbd>Shift</kbd> + drag a handler of the selection area: mirror redimension in the opposite handler.

### Global
If you want use Flameshot as a default screenshot utility, chances are you want to launch it using the <kbd>Prt Sc</kbd> key. Flameshot doesn't yet offer a fully-automated option to do so, but you can configure your system to do so.

#### On KDE Plasma desktop
To make configuration easier, there's a [file](https://github.com/lupoDharkael/flameshot/docs/shortcuts-config/flameshot-shortcuts-kde) in the repository that more or less automates this process. This file will assign the following keys to the following actions by default:

|  Keys                                                           |  Description                                                                                |
|---                                                              |---                                                                                          |
| <kbd>Prt Sc</kbd>                                               | Start the Flameshot screenshot tool and take a screenshot                                   |
| <kbd>Ctrl</kbd> + <kbd>Prt Sc</kbd>                             | Wait for 3 seconds, then start the Flameshot screenshot tool and take a screenshot          |
| <kbd>Shift</kbd> + <kbd>Prt Sc</kbd>                            | Take a full-screen (all monitors) screenshot and save it                                    |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Prt Sc</kbd>          | Take a full-screen (all monitors) screenshot and copy it to the clipboard                   |

If you don't like the defaults, you can change them manually later.

Steps for using the configuration:

1. The configuration file configures shortcuts so that Flameshot automatically saves (without opening the save dialog) screenshots to _~/Pictures/Screenshots_ folder. Make sure you have that folder by running the following command:
    ```
    mkdir -p ~/Pictures/Screenshots
    ```
   (If you don't like the default location, you can skip this step and configure your preferred directory later.)

2. Download the configuration file:
    ```
    cd ~/Desktop; wget https://raw.githubusercontent.com/lupoDharkael/flameshot/master/docs/shortcuts-config/flameshot-shortcuts-kde
    ```
3. Go to _System Settings_ → _Shortcuts_ → _Custom Shortcuts_.
4. If there's one, you'll need to disable an entry for Spectacle, the default KDE screenshot utility first because its shortcuts might collide with Flameshot's ones; so, just uncheck the _Spectacle_ entry.
5. Click _Edit_ → _Import..._, navigate to the Desktop folder (or wherever you saved the configuration file) and open the configuration file.
6. Now the Flameshot entry should appear in the list. Click _Apply_ to apply the changes.
7. If you want to change the defaults, you can expand the entry, select the appropriate action and modify it as you wish; the process is pretty mush self-explanatory.