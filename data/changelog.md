## v0.6.0
>2018.08.17

### Features:
* Allow systray customization with themes. Use "flameshot-tray" as the name of the icon.
* Unification of the desktop file with actions.
* Notification when screenshots are saved in the clipboard.
* Use datetime as default name for pics.
* Undo/Redo with Ctrl+z and Ctrl+Shift+z.
* Add "Take Screenshot" option as menu item in the systray.
* Add Side-Panel (open it with Space).
* Add autostart to config flags.
* Add Pin tool.
* Filename: replace colons with dashes.
* Add Text tool.
* Delete Imgur image button after uploading it from the preview window.
* Capture single screen:
* flameshot screen (capture the screen containing the mouse) and
* flameshot screen -n 1 (capture the first screen).
* Store settings colors in hexadecimal format.

### Fixes
* flameshot full -c shouldn't block the desktop.
* Now you can overwrite exported configuration with the same name as a previous exports.
* Fix flameshot --raw wait time with delay.
* Fix negative selection geometry bug.
* Improved hidpi support with some bugs fixed.

## v0.5.1
>2018.02.24

### Features:
* Polish, French, Georgian, Chinese, Turkish and Rusian translations
* Modal widgets doesn't prevent the start of a new capture
* Improved hidpi support (still needs some work)
* Tool buttons now don't go out of the screen
* Use of native file dialog
* Configurable opacity of the dark area outside the selection
* Autostart app as a configuration option

### Fixes
* Minor fixes

## v0.5.0
>2017.12.20

### Features
* Catalan translation.
* Debian package configuration.
* Add --raw flag: prints the raw bytes of the png after the capture.
* Bash completion.
* Blur tool.
* Preview draw size on mouse pointer after tool selection.
* App Launcher tool: choose an app to open the capture.
* Travis integration
* Configuration import, export and reset.
* Experimental Wayland support (Plasma & Gnome)

### Accesibility
* Capture selection resizable using any border.

### Fixes
* App version shown properly
* Now the cli wont break if you preppend a dash before gui, full and config arguments.
* Fix rare crash condition creating a selection during a graphical capture.

## v0.4.2
>2017.09.17

### Hotfix: 
* persistent configuration wasn't handled correctly for new users, failing to set a "initiated" status flag in the configuration. That is used to let the program know if a new process of Flameshot is the first launch of the program.

## v0.4.1
>2017.08.29

### Features
* Slightly darker capture background (Cross cursor more visible in Plasma)
* Flameshot compiles with QT 5.3 (Debian 8, Linux Mint, etc)

## v0.4.0
>2017.08.17

### Features
* The buttons hide when you have selected the whole screen and you try to draw behind them.
* Add informative labels in the filename editor.
* A better CLI parser with a more effective (and informative) syntax error handling.
* new CLI argument 'config' to manage some configurations from terminal.
* More uniform button's hovering color.
* Automatic horizontal adjustment in Marker and Line tools.
* Enhanced menus with expandable layouts.
* Add graphical option to disable the trayicon.
* Now you can check the version of Flameshot!
* Shrink the selection area when pushing against the borders of the screen.
* Now you can change the thickness of the drawing tools using the mouse wheel!
* Some more little changes.

### Fixes
* Fix button's emerge animation while hovering.
* Fix freeze problem with save dialog and clipboard copy at the same time.
* Minor Fixes

### Extras
* More code cleanup! (still more to do)

## v0.3.0
>2017.07.25

### Features
* Add Desktop entry to init flameshot without commands.
* New configuration menu design.
* Define custom names for your captures!
* Improved error notifications when saving captures.

### Fixes
* Multiple monitor support.
* Makefile flag for custom installs (packaging)
* Non blocking error notifications.
* Add error notifications for Imgur uploads.
* Minor Fixes

### Extras
* Huge general code refactor.
* Dbus API refactor.

## v0.2.1
>2017.07.04

### Fixes
* Fix inability to change active buttons in non english translated versions of the software due to a wrong identification of the type of the buttons.

## v0.2.0
>2017.06.20

### Features
* Better selection of buttons for colour edition.
* Independence of full screen captures not affecting the graphical captures.
* Desktop entry for a more convenient desktop integration.

## v0.1.0
>2017.06.19

### Features
* First public release.