+++
title = "Overview"
description = ""
date = 2021-05-01T19:30:00+00:00
updated = 2021-05-01T19:30:00+00:00
draft = false
weight = 30
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "An overview of Flameshot."
toc = true
top = false
+++


> Powerful yet simple to use screenshot software.

- Customizable appearance.
- Easy to use.
- In-app screenshot edition.
- DBus interface.
- Upload to Imgur.

## Considerations

- Experimentally **Gnome Wayland** and **Plasma Wayland** support.
- If you are using Gnome you need to install the [TopIcons](https://extensions.gnome.org/extension/1031/topicons/) extension in order to see the systemtray icon.
- In order to speed up the first launch of Flameshot (DBus init of the app can be slow), consider starting the application automatically on boot.
- Press <kbd>Ctrl</kbd> + <kbd>C</kbd> when you are in a capture mode and you don't have an active selection and the whole desktop will be copied to your clipboard! Pressing <kbd>Ctrl</kbd> + <kbd>S</kbd> will save your capture in a file! Check the [Shortcuts](/guide/key-bindings/#keyboard-shortcuts) for more information.
- Execute the command `flameshot` without parameters or use the "Launch Flameshot" desktop entry to launch a running instance of the program without taking actions.

## License

- The main code is licensed under [GPLv3](https://github.com/flameshot-org/flameshot/LICENSE)
- The logo of Flameshot is licensed under [Free Art License v1.3](https://github.com/flameshot-org/flameshot/img/flameshotLogoLicense.txt)
- The button icons are licensed under Apache License 2.0. See: https://github.com/google/material-design-icons
- The code at capture/capturewidget.cpp is based on https://github.com/ckaiser/Lightscreen/blob/master/dialogs/areadialog.cpp (GPLv2)
- The code at capture/capturewidget.h is based on https://github.com/ckaiser/Lightscreen/blob/master/dialogs/areadialog.h (GPLv2)
- Copied a few lines of code from [KSnapshot](https://github.com/KDE/ksnapshot) regiongrabber.cpp revision 796531 (LGPL)
- Qt-Color-Widgets taken and modified from https://github.com/mbasaglia/Qt-Color-Widgets (see their license and exceptions in the project) (LGPL/GPL)

Info: If I take code from your project and that implies a relicense to GPLv3, you can reuse my changes with the original previous license of your project applied.
