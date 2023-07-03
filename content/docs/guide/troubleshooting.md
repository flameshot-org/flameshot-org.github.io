+++
title = "Troubleshooting"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:20:00+00:00
updated = 2022-05-29T08:20:00+00:00
draft = false
weight = 1
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

In case you didn't find similar issue, create a new issue and explain in detail what the issue is. If you can, add pictures or video recordings to clarify the situation. For bug reports, make sure to also visit the [issue reporting page](../issue-reporting) in which we have explained how to get the information we need in each bug report.

--------------------------------------------------------------------------------

## Linux


### I have fractional scaling on my monitors (e.g. 150%)

It has been reported numerous times on various display servers and window managers that when the fractional scaling is on, Flameshot does not correctly capture and show the screenshot. [[1](https://github.com/flameshot-org/flameshot/issues/564), [2](https://github.com/flameshot-org/flameshot/issues/724), [3](https://github.com/flameshot-org/flameshot/issues/748)]. The solution that the community provided so far is to try to modify an environment variable when running Flameshot. For example:

```sh
env QT_AUTO_SCREEN_SCALE_FACTOR=1.5 QT_SCREEN_SCALE_FACTORS="" flameshot gui
```


### In the System tray area, Flameshot appears to have duplicate icons/indicator

It is currently known that in Ubuntu 14.04 and 16.04 Unity environments such problems occur. This problem does not occur with Ubuntu 17.10 Unity. [#92](https://github.com/flameshot-org/flameshot/issues/92)


### In **Gnome** the Flameshot icon does not appear in the tray

Gnome does not have a systray, therefore in Gnome you should install the gnome [Tray icons](https://extensions.gnome.org/extension/1503/tray-icons/) extension. For more information, read the [Tray icon](https://github.com/flameshot-org/flameshot#tray-icon) section of the github repository.


### In **tiling window managers** (e.g i3wm, dwm, bspwm) Flameshot crashes when taking the screenshot

Most tiling window managers do not come with a notification daemon, and Flameshot communicates with the user through notifications. This means that Flameshot is dependent on a notification manager to be installed and running. Easy way to test if you have a notification manager is to try `notify-send "test"` in your terminal. If you see the notification, you have it, otherwise we suggest you to install a notification manager such as `dunst`:

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

This can be because the window manager is forcing to tile Flameshot. This can be solved by defining window rule. For example for Sway the following rule is suggested in [#2364](https://github.com/flameshot-org/flameshot/issues/2364#issuecomment-1086129055):

```py
for_window [app_id="flameshot"] border pixel 0, floating enable, fullscreen disable, move absolute position 0 0
```

### Flameshot icon is visible in tray area but when I click on it nothing happens

* First try the using the command `flameshot gui` in terminal. This does exactly what clicking on the tray icon does (make sure can you see Flameshot icon in the tray area).

* If the step above didn't work:
    1. Open **3** terminals
    2. Kill Flameshot if it is already open using:
        ```sh
        pkill flameshot
        ```
    3. In the **first terminal** run:
       ```sh
       dbus-monitor --session sender=org.flameshot.Flameshot
       ```
    4. In the **second terminal** run:
       ```sh
        flameshot
        ```
    5. In the **third terminal** run the command you want us to investigate. For example:
        ```sh
        flameshot gui
        ```
    6. Copy the following into the text of your Github issue:
        ````html
        <details>
        <summary>The dbus-monitor content</summary>
        
        ```
        
        REPLACE THIS LINE WITH YOUR DBUS LOG
        
        ```
        
        </details>
        ````
    7. Replace the line in the middle with the content of the **first terminal**

This way we can see how different parts of flameshot are communicating with each other and resolve the issue. We encourage you to read this short log file and make sure there is nothing personal in it (it should not contain personal info anyways).


### In **Xfce** sometimes Flameshot does not let me select screenshot area

It has been confirmed by multiple users that the compositor is at fault [#629](https://github.com/flameshot-org/flameshot/issues/629#issuecomment-989136575). It has been suggested to disable "Display fullscreen overlay windows directly". You just need to open "Window Manager Tweaks" in your Xfce, go to the "Compositor" tab and remove the checkmark from "Display fullscreen overlay windows directly".


### In **Gnome** keybinding to run flameshot does not work

It has been reported that users have tried to bind a keybinding in their Gnome settings to start Flameshot, but nothing opens, although when they run the same command in terminal it works just fine (e.g [issue #3253](https://github.com/flameshot-org/flameshot/issues/3252)). If in the command you are using `~` or `$HOME` to tell flameshot where to save the file, then the reason is that, unlike KDE, Gnome does not expand environmental variables. You can easily test it by using `notify-send "this is test" "$HOME"` in the keybinding. The solution is to use the full path and avoid any environmental variables.


--------------------------------------------------------------------------------

## macOS

### All opened applications go away and only the blank desktop is visible for selection

As it has been reported multiple times already ([1](https://github.com/flameshot-org/flameshot/issues/1537), [2](https://github.com/flameshot-org/flameshot/issues/1571)), macOS restricts applications from accessing the screen. Therefore you have to give Flameshot security permissions to "record" your desktop.

![A picture of the macOS Security & Privacy settings that shows the Flameshot should be added to the list in the "privacy" tab](/media/macos_permissions.png)

If you were still getting the following message when restarting Flameshot, try removing (using the "-" button) and then adding Flameshot to the list above.

![A screenshot of a permission request window in macOS which says "Flameshot.app would like to record this computer's screen"](/media/macos_screenrecording_permission_request.png)

When this step is done you have to restart your macOS to make the permissions get working. This has been an issue of macOS that many users have reported, hopefully this macOS bug will be addressed by Apple, but until that day, the only easy solution is rebooting.


### The command `flameshot` does not exist in my terminal

In general to have a command in your shell (e.g zsh) you should put the binary in your path. You can see your paths by `echo $PATH` (note that they are separated by `:`). You can either:
1. create a symlink to Flameshot binary in one of those folders listed (check out `man ln`)
2. add the folder that contains Flameshot to your path (`export PATH="path/to/your/folder:$PATH"`). If you have installed Flameshot using the DMG we provide, Macports, or Homebrew, you most probably have it located in `/Applications/flameshot.app/`.


### Flameshot only works on the primary screen

Depending on how you have Spaces configured in Mission Control you may only be able to activate Flameshot on a particular external display by using the `shift+alt+cmd+4` hotkey. Otherwise, Flameshot will only activate on the main display if you click "Take Screenshot" from the application menu. Fix it by uninstalling, installing again and selecting Flameshot again in the `Screen Recording` section. (reported to work [here](https://github.com/flameshot-org/flameshot/issues/1258#issuecomment-1004297496))

--------------------------------------------------------------------------------

## Windows

### Command line arguments do not work

At the time of writing this (version 11.0.0), the command line is not implemented for Windows. We might add it in future versions. You can follow the discussions/development of this feature in [#2118](https://github.com/flameshot-org/flameshot/issues/2118).

In the meanwhile you can use [AutoHotKey](https://www.autohotkey.com/) as [explained here](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-1126669379).


### Flameshot does not launch at startup even when the settings are set

As [explained by @HoshyarKarimi](https://github.com/flameshot-org/flameshot/issues/2422#issuecomment-1140393544) (this should only be done once):


1. From the configuration uncheck "Launch at startup"
2. Quit Flameshot from system tray
3. Now run Flameshot _as administrator_
4. Open the configuration and check the "Launch at startup" box

The settings should now be set. You can close Flameshot from the system tray and use it normally from here after.


### PrintScreen key opens Snip tool instead of Flameshot

The following solution [was provided](https://github.com/flameshot-org/flameshot/issues/1551#issuecomment-1166317630) by a member of our community:

1. set `Computer\HKEY_CURRENT_USER\Control Panel\Keyboard\PrintScreenKeyForSnippingEnabled` to 0
2. set `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\TabletPC\DisableSnippingTool` to 1 (skip this step if you don't have the `\TabletPC\`)
3. uninstall "Snip and Sketch" via the Microsoft Store
