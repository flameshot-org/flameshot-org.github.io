# Troubleshooting

Please first read the troubleshooting steps for your operating system in this page and then if it was not solved, report the issue after reading the [Issue reporting section](#issue-reporting) down below:

*Table of Content*
- [Issue reporting](#issue-reporting)
- [Linux](#linux)
- [macOS](#macos)


## Issue reporting

To report a bug or suggest a new feature, you can go to [GitHub issues page](https://github.com/flameshot-org/flameshot/issues) and use the searchbox in the middle of the page to see if anyone else have already posted something similar. Sometimes you will find a quick solution just by reading the threads. In case of feature request, if you find someone with similar idea, just give that a thumbs-up to increase its priority/importance.

In case you didn't find similar issue, create a new issue and explain in details what the issue is. If you can, add pictures or video recordings to clarify the situation. For bug reports, make sure to also visit [issue reporting page](/issue-reporting) in which we have explained how to get the information we need in each bug report.

-------

## Linux

### In System tray area, flameshot appears **duplicate icons/indicator**

* It is currently found in Ubuntu 14.04 and 16.04 Unity environment, such problems occur. This problem does not occur with Ubuntu 17.10 Unity. [#92](https://github.com/flameshot-org/flameshot/issues/92)


### In Gnome the flameshot icon does not appear in the tray

* Gnome does not have a systray, therefore in Gnome you should install the gnome [Tray icons](https://extensions.gnome.org/extension/1503/tray-icons/) extension. For more information, read the [Tary icon](https://github.com/flameshot-org/flameshot#tray-icon) section of the github repository.

### In tiling window managers (e.g i3wm, dwm, bspwm) flameshot crashes when taking the screenshot

* most tiling window managers dows not come with a nitification daemon, and Flameshot communicates with user through notifications. This means that Flameshot is dependent on notification manager to be installed and running. Easy way to test if you have a notification manager is to try `notify-send "test"` in your terminal. If you see the notification, you have it, otherwise we suggest you to install a notification manager such as `dunst`:

https://github.com/flameshot-org/flameshot/issues/1179#issuecomment-757544326

### Flameshot icon is visible in tray area but when I click on it nothing happens

* First try the using the command `flameshot gui` in terminal. This does exactly what clicking on the tray icon does. (make sure can you see Flameshot icon in the tray area)

* If the above step didn't work:
    1. Open 3 terminals
    2. Kill Flameshot if it is already open using `pkill flameshot`
    3. In the first terminal run `dbus-monitor --session sender=org.flameshot.Flameshot`
    4. In the second terminal run `flameshot`
    5. In the third terminal run `flameshot gui`
    6. Copy the content of the first terminal in pastebin: https://bin.snopyta.org/
    - ![image](https://user-images.githubusercontent.com/390889/116671105-3b09d780-a9a9-11eb-8941-df52c9802c85.png)
    7. Post the link in the [issue on Github](https://github.com/flameshot-org/flameshot/issues)

-------

## macOS

### All opened applications go away and only the blank desktop is visible for selection

As it has been reported multiple times already ([1](https://github.com/flameshot-org/flameshot/issues/1537), [2](https://github.com/flameshot-org/flameshot/issues/1571)), macOS restricts applications from accessing the screen. Therefore you have to give Flameshot security permissions to "record" your desktop.

![A picture of the macOS Security & Privacy settings that shows the Flameshot should be added to the list in the "privacy" tab](/media/macos_permissions.png)

If you were still getting the following message when restarting Flameshot, try removing (using the "-" button) and then adding flameshot to the list above.

![A screenshot of a permission request window in macOS which says "Flameshot.app would like to record this computer's screen"](/media/macos_screenrecording_permission_request.png)

### The command `flameshot` does not exist in my terminal

- In general to have a command to your shell (e.g zsh) you should put the binary in your path. You can see your paths by `echo $PATH` (note that they are separated by `:`. You can either:
                                                                                                                                1. create a symlink to flameshot binary in one of those folder listed (check out `man ln`)
                                                                                                                                2. add the folder that contains Flameshot to your path (`export PATH="path/to/your/folder:$PATH"`). If you have installed Flameshot using the DMG we provid, Macports, or Homebrew, you most probably have it located in `/Applications/flameshot.app/`.
