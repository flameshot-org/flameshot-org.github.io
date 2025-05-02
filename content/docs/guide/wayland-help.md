+++
title = "Wayland Help"
description = "A page to help Wayland users sort out some Wayland-specific issues"
date = 2022-01-28T16:31:10+00:00
updated = 2022-09-13T17:58:00+00:00
draft = false
weight = 1
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "Troubleshooting Flameshot on Wayland"
toc = true
top = false
+++


In this page you can find possible solutions for issues on Wayland. This page probably needs frequent update, so if something was outdate, please [report it here](https://github.com/flameshot-org/flameshot-org.github.io/issues/new).


**Disclaimer:** Of course it should go without saying that it is not a good idea to run a code you find online on your computer without understanding it. So run the code presented here at your own risk. We try to vet all the code snippets on this website, but it is always possible that we miss something. To be clear, your computer and the code your decide to run on it is your responsibility. 


# Gnome Wayland

## I am asked to "Share" my screen every time

![gnome permission window](/media/content/docs/guide/wayland-help/2022-08-04_11-39_gnome_share_permission_indow.png "Screenshot of the Gnome permission window which has a Share button at the top right corner")

If you are a Gnome 41 (or later) user, know that you are not alone in this as many have brought up this issue ([example](https://github.com/flameshot-org/flameshot/issues/2186)). This is **NOT** a Flameshot bug nor it was our decision. This is something that Gnome developers unilaterally and suddenly implemented and this is affecting **ALL** screenshot tools other than the Gnome default screenshot tool (they have white-listed their own software). For more information please read the following:

- <https://github.com/flameshot-org/flameshot/issues/2186>
- <https://gitlab.gnome.org/GNOME/gnome-shell/-/merge_requests/1970>
- <https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/4895>
- <https://github.com/flatpak/xdg-desktop-portal/issues/649>

Therefore please **do not** waste your time ([like many have](https://github.com/flameshot-org/flameshot/issues?q=is%3Aissue+is%3Aclosed+label%3ADuplicate+label%3A%22Won%27t+Fix%22+gnome+)) by complaining to Flameshot developers. We cannot do anything about it! If you want this issue to change, please take your complaints to [here](https://gitlab.gnome.org/GNOME/gnome-shell/-/merge_requests/1970) and [here](https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/4895).

Thank you!


## Can't screen anything on Wayland Gnome

**Symptom:** Launcher (right-click on tray icon, then "Open Launcher") does not show anything in the preview section (left-side of the window)

You install `xdg-desktop-portal-gnome` and `xdg-desktop-portal`.


## Gnome shortcut does not trigger Flameshot

**Symptom:** When using a shortcut (Print screen) to run Flameshot I get "Unable to capture screen". When I run the command from the shortcut in a terminal, it works. Both used to work fine before, but stopped working after my daily updates. The normal Gnome screenshot program still works. [[source](https://github.com/flameshot-org/flameshot/issues/3365)]

We don't have a definite answer of what in Gnome have changed, but Gnome users have provided the following solution:

Run the `flameshot gui` via a shell script

```sh
script --command "QT_QPA_PLATFORM=wayland flameshot gui" /dev/null
# or
bash -c -- "QT_QPA_PLATFORM=wayland flameshot gui"
# or
sh -c -- "QT_QPA_PLATFORM=wayland flameshot gui"
```

If this didn't solve your issue or if you are not sure what you do about this, Best places to look for are [#3365](https://github.com/flameshot-org/flameshot/issues/3365) and [#3326](https://github.com/flameshot-org/flameshot/issues/3326).

In general, these specific comments worth your attention:

- https://github.com/flameshot-org/flameshot/issues/3326#issuecomment-1789267986
- https://github.com/flameshot-org/flameshot/issues/3326#issuecomment-1826336292
- https://github.com/flameshot-org/flameshot/issues/3365#issuecomment-1928940359
- https://github.com/flameshot-org/flameshot/issues/3365#issuecomment-1930538662
- https://github.com/flameshot-org/flameshot/issues/3365#issuecomment-1817581463
- https://github.com/flameshot-org/flameshot/issues/3365#issuecomment-1810832381
- [Specifically for NixOS users](https://github.com/flameshot-org/flameshot/issues/3365#issuecomment-1868580715)


## Reset Gnome shortcut permission

In Gome Wayland the users is asked if they want to give permission to the screenshot tool to capture the screen. It is possible to hit the wrong button and permanently block Flameshot from taking the screenshot. The workaround [have been proposed by the community](https://github.com/flameshot-org/flameshot/issues/3365#issuecomment-2823998280). Running the following command in terminal would reset the permission in Gnome Wayland:

```sh
dbus-send --session  --print-reply=literal --dest=org.freedesktop.impl.portal.PermissionStore /org/freedesktop/impl/portal/PermissionStore org.freedesktop.impl.portal.PermissionStore.D
eletePermission string:'screenshot' string:'screenshot' string:''
```

--------------------------------------------------------------------------------

# KDE Wayland

## 4k displayed and fractional scaling

It has been [reported](https://github.com/flameshot-org/flameshot/issues/227#issuecomment-1002696986) that setting the environmental variable `QT_SCREEN_SCALE_FACTORS` to `1;1` can solve the issue. You can do the following every time your computer boots:

```sh
export QT_SCREEN_SCALE_FACTORS="1;1"
```

and then you can normally use Flameshot (e.g `flameshot gui`)

## Can't screen anything on Wayland KDE

**Symptom:** Launcher (right-click on tray icon, then "Open Launcher") does not show anything in the preview section (left-side of the window)

You install `xdg-desktop-portal-kde` and `xdg-desktop-portal`.
