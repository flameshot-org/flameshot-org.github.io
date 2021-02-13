## Linux

### In System tray area, flameshot appears **duplicate icons/indicator**

* It is currently found in Ubuntu 14.04 and 16.04 Unity environment, such problems occur. This problem does not occur with Ubuntu 17.10 Unity. [#92](https://github.com/flameshot-org/flameshot/issues/92)


### In Gnome the flameshot icon does not appear in the tray

* Gnome does not have a systray, therefore in Gnome you should install the gnome [Tray icons](https://extensions.gnome.org/extension/1503/tray-icons/) extension. For more information, read the [Tary icon](https://github.com/flameshot-org/flameshot#tray-icon) section of the github repository.

### In tiling window managers (e.g i3wm, dwm, bspwm) flameshot crashes when taking the screenshot

* most tiling window managers dows not come with a nitification daemon, and Flameshot communicates with user through notifications. This means that Flameshot is dependent on notification manager to be installed and running. Easy way to test if you have a notification manager is to try `notify-send "test"` in your terminal. If you see the notification, you have it, otherwise we suggest you to install a notification manager such as `dunst`:

https://github.com/flameshot-org/flameshot/issues/1179#issuecomment-757544326


