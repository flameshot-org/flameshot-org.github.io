+++
title = "Troubleshooting"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:20:00+00:00
updated = 2022-05-29T08:20:00+00:00
draft = false
weight = 3
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "Troubleshooting Flameshot."
toc = true
top = false
+++


Please first read the troubleshooting steps for your operating system in this page and then if it was not solved, report the issue after reading the [Issue reporting section](#issue-reporting) down below.

## Issue reporting

To report a bug or suggest a new feature, you can go to [GitHub issues page](https://github.com/flameshot-org/flameshot/issues) and use the searchbox in the middle of the page to see if anyone else have already posted something similar. Sometimes you will find a quick solution just by reading the threads. In case of feature request, if you find someone with similar idea, just give that a thumbs-up to increase its priority/importance.

In case you didn't find similar issue, create a new issue and explain in details what the issue is. If you can, add pictures or video recordings to clarify the situation. For bug reports, make sure to also visit the [issue reporting page](../issue-reporting) in which we have explained how to get the information we need in each bug report.

--------------------------------------------------------------------------------

## Linux

### In the System tray area, flameshot appears to have duplicate icons/indicator

It is currently found in Ubuntu 14.04 and 16.04 Unity environment, such problems occur. This problem does not occur with Ubuntu 17.10 Unity. [#92](https://github.com/flameshot-org/flameshot/issues/92)

### In **Gnome** the flameshot icon does not appear in the tray

* Gnome does not have a systray, therefore in Gnome you should install the gnome [Tray icons](https://extensions.gnome.org/extension/1503/tray-icons/) extension. For more information, read the [Tary icon](https://github.com/flameshot-org/flameshot#tray-icon) section of the github repository.

### In **tiling window managers** (e.g i3wm, dwm, bspwm) Flameshot crashes when taking the screenshot

* most tiling window managers dows not come with a nitification daemon, and Flameshot communicates with user through notifications. This means that Flameshot is dependent on notification manager to be installed and running. Easy way to test if you have a notification manager is to try `notify-send "test"` in your terminal. If you see the notification, you have it, otherwise we suggest you to install a notification manager such as `dunst`:

https://github.com/flameshot-org/flameshot/issues/1179#issuecomment-757544326

### In **tiling window managers** (e.g i3wm, dwm, bspwm) Flameshot does not pin the screenshot

This is simply because you have not started the DBus. Either run `dbus-launch dwm` (or any other window manager/desktop environment) at startup, or run Flameshot daemon (`flameshot`) before taking the screenshot. For example:

```sh
# this will start the daemon
flameshot &
# this will select a 300 by 200 pixel area, and immediately pin it
flameshot gui --region 300x200+300+300 --pin --accept-on-select 
```

### In **tiling window managers** (e.g i3wm, dwm, bspwm) Flameshot only appears on a single monitor

This can be because the window manager is forcing to tile FLameshot. This can be solved by defining window rule. For example for Sway the following rule is suggested in [#2364](https://github.com/flameshot-org/flameshot/issues/2364#issuecomment-1086129055):

```py
for_window [app_id="flameshot"] border pixel 0, floating enable, fullscreen disable, move absolute position 0 0
```

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

## In **Xfce** sometimes it doesn't let me to select area

It has been confirmed by multiple users that the compositor is at fault [#629](https://github.com/flameshot-org/flameshot/issues/629#issuecomment-989136575). It has been suggested to disable "Display fullscreen overlay windows directly". You just need to open "Window Manager Tweaks" in your Xfce, go to the "Compositor" tab and remove the checkmark from "Display fullscreen overlay windows directly".

--------------------------------------------------------------------------------

## macOS

### All opened applications go away and only the blank desktop is visible for selection

As it has been reported multiple times already ([1](https://github.com/flameshot-org/flameshot/issues/1537), [2](https://github.com/flameshot-org/flameshot/issues/1571)), macOS restricts applications from accessing the screen. Therefore you have to give Flameshot security permissions to "record" your desktop.

![A picture of the macOS Security & Privacy settings that shows the Flameshot should be added to the list in the "privacy" tab](/media/macos_permissions.png)

If you were still getting the following message when restarting Flameshot, try removing (using the "-" button) and then adding flameshot to the list above.

![A screenshot of a permission request window in macOS which says "Flameshot.app would like to record this computer's screen"](/media/macos_screenrecording_permission_request.png)

When this step is done you have to restart your macOS to make the permissions get working. This has been an issue of macOS that many users have reported, hopefully this macOS bug will be addressed by Apple, but until that day, the only easy solution is rebooting.

### The command `flameshot` does not exist in my terminal

- In general to have a command to your shell (e.g zsh) you should put the binary in your path. You can see your paths by `echo $PATH` (note that they are separated by `:`). You can either:
                                                                                                                                1. create a symlink to flameshot binary in one of those folder listed (check out `man ln`)
                                                                                                                                2. add the folder that contains Flameshot to your path (`export PATH="path/to/your/folder:$PATH"`). If you have installed Flameshot using the DMG we provide, Macports, or Homebrew, you most probably have it located in `/Applications/flameshot.app/`.

### Flameshot only works on the primary screen

depending on how you have Spaces configured in Mission Control you may only be able to activate flameshot on a particular external display by using the `shift+alt+cmd+4` hotkey. Otherwise, flameshot will only activate on the main display if you click "Take Screenshot" from the application menu. Fix it by uninstalling, installing again and selecting flameshot again in the `Screen Recording` section. (reported to work [here](https://github.com/flameshot-org/flameshot/issues/1258#issuecomment-1004297496))
                                                                                                                             --------------------------------------------------------------------------------

## Windows

### Commandline arguments does not work

At the time of writing this (version 11.0.0), the commandline is not implemented for Windows. We might add it in future versions. You can follow the discussions/development of this feature in [#2118](https://github.com/flameshot-org/flameshot/issues/2118).

In the meanshile you can use [AutoHotKey](https://www.autohotkey.com/) as [explained here](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-1126669379).


### Does not launch at startup even when the settings is set

As [explained by @HoshyarKarimi](https://github.com/flameshot-org/flameshot/issues/2422#issuecomment-1140393544) (this should only be done once):


1. From the configuration uncheck Launch at startup
2. Quit Flameshot from system tray
3. Now run Flameshot _as administrator_
4. Open the configuration and check the Launch at startup box

The settings should now be set. You can close Flameshot from the system tray and use it normally from here after.

