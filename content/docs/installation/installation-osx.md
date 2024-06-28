+++
title = "Install on macOS"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2024-05-30T08:00:00+00:00
draft = false
weight = 2
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'How to install Flameshot on macOS.'
toc = true
top = true
+++

## Installation on macOS (OSXI)

You can install Flameshot on [macOS](https://en.wikipedia.org/wiki/MacOS) using the either of the following:

- [MacPorts](https://ports.macports.org/port/flameshot/summary): `sudo port selfupdate && sudo port install flameshot`
- [Homebrew](https://formulae.brew.sh/cask/flameshot): `brew install --cask flameshot`
    > Note that because of macOS security features, you may not be able to open flameshot when installed using brew. If you see the message `“flameshot” cannot be opened because the developer cannot be verified.` you will need to follow the steps below:
    >
    > 1. Go to the Applications folder (Finder > Go > Applications, or Shift+Command+A)
    > 2. Right-Click on `flameshot.app` and choose `Open` from the context menu
    > 3. In the dialog click `Open`
    >
    > After following all those steps above, flameshot will open without problems in your Mac.
- Download DMG file:
    1. Navigate to [the release page on Github](https://github.com/flameshot-org/flameshot/releases)
    2. From the assets of the latest stable release, download the latest DMG file
    3. Double-click on the DMG file you downloaded
    4. Drag and drop the `flameshot.app` to your `/Applications` folder
    5. macOS restricts applications from accessing the screen. Therefore you have to give Flameshot security permissions to "record" your desktop.
        ![A picture of the macOS Security & Privacy settings that shows the Flameshot should be added to the list in the "privacy" tab](/media/macos_permissions.png)
