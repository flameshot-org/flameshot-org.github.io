+++
title = "FAQ"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 4
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'Frequently asked questions about common problems with Flameshot and how to solve them.'
toc = true
top = false
+++

## Flameshot freezes after capturing an image

By default Flameshot requires a notification manager. Notifications are sent to the notification manager via d-bus. If either d-bus or the notification manager is not properly configured, Flameshot will freeze for 30 seconds.

Fix 1: Install a notification manager

Fix 2: Manually edit the config file at ``~/.config/flameshot/flameshot.ini`` and add the following line: ``showDesktopNotification=false``

## Flameshot doesn't start / no tray icon

When Flameshot is started with a system launcher or from the CLI it starts a daemon in the background. To interact with this daemon through a graphical client your desktop environment **must support a system tray**. See the README for tips on setting up a system tray.

This sometimes causes pain for Arch users running Gnome, because the system tray extension becomes out of sync with gnome upon a new gnome release. **Please do not report this as a bug in Flameshot.** We are reliant on a system tray and have no intention to change this.

## On MacOs Flameshot only captures a blank desktop¶

When running Flameshot on MacOs, you must grant it permission to screen record. See [troubleshooting](../troubleshooting#macos) for more information.

## With fractional scaling my screen appears shifted
There is a known issue in Qt related to fractional scaling and full screen applications. We are hoping this is resolved in Qt6. See [this post](https://forum.qt.io/topic/121111/position-of-widget-with-fractional-scaling) for more details.

## On Linux using Cinnamon, the tray icon does not show
It seems there is a bug in Cinnamon that creates a loading race which will cause some software to load before the tray area is loaded. The solution [as proposed by a Cinnamon user](https://github.com/flameshot-org/flameshot/issues/1648#issuecomment-891612360) is to create a loading delay for all the applications that are affected by this bug: for all the `.desktop` files in `~/.config/autostart` in the `"[Desktop Entry]` section add the following line (you can try reducing the delay and check what is the optimal value for your computer as it can depend on the load, computational power and disk IO):

```bash
X-GNOME-Autostart-Delay=3
```