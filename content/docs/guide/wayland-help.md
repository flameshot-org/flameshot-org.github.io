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
