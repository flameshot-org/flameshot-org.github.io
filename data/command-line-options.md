## Usage
Example commands:
- capture with GUI:

   `flameshot gui`

- capture with GUI with custom save path:

   `flameshot gui -p ~/myStuff/captures`

- open GUI with a delay of 2 seconds:

   `flameshot gui -d 2000`

- fullscreen capture (asking savepath):

   `flameshot full`

- fullscreen capture with custom save path (no GUI) and delayed:

   `flameshot full -p ~/myStuff/captures -d 5000`

- fullscreen capture with custom save path copying to clipboard:

   `flameshot full -c -p ~/myStuff/captures`

In case of doubt choose the first or the second command as shortcut in your favorite desktop environment.

A systray icon will be in your system's panel while Flameshot is running.
Do a right click on the tray icon and you'll see some menu items to open the configuration window and the information window.
Check out the information window to see all the available shortcuts in the graphical capture mode.


## CLI configuration
You can use the graphical menu to configure Flameshot, but alternatively you can use your terminal or scripts to do so.

- open the configuration menu:

   `flameshot config`

- show the initial help message in the capture mode:

   `flameshot config --showhelp true`

- for more information about the available options use the help flag:

   `flameshot config -h`