+++
title = "Microsoft Windows Help"
description = "A page to help Windows users sort out Windows-specific issues"
date = 2022-08-31T12:30:37+03:00
updated = 2022-08-31T12:30:46+03:00
draft = false
weight = 1
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "Windows-specific guides"
toc = true
top = false
+++


In this page you can find possible solutions for issues on Windows. This page probably needs frequent update, so if something was outdate, please [report it here](https://github.com/flameshot-org/flameshot-org.github.io/issues/new).

# Keyboard shortcuts

## How to disable Windows Snipping tool when I press PrintScreen

As kindly [explained by one of our users](https://github.com/flameshot-org/flameshot/issues/1551#issuecomment-1232164940), you can disable the built-in snipping tool by going to Windows Settings -> Ease of Access -> Keyboard -> Scroll down to "Print Screen Shortcut" and turn off the "Use the Prtscn button to open screen snipping":

![Windows settings screenshot](/media/content/docs/guide/windows-help/disable-windows-snipping-tool.png)


## Setting up custom shortcut to start Flameshot

Windows is pretty limitted, but there is a way to make windows to run a software based on a keybinding. To do this, you have to:
1. create a shortcut file (right-click on Desktop > New > Shortcut)
2. in the "Target" field, add the software you want to run with keybinding (in this case the path to the `flameshot.exe`)
3. in the "Shortcut key" field, type the keybinding you want (e.g `Ctrl + Alt + p`)

For a more detailed instruction, visit [this article from the Digital Citizen](https://www.digitalcitizen.life/start-windows-apps-keyboard-shortcut/).

-------

# CommandLine Interface

For the time being, the Commandline Interface (CLI) is **not** implemented for Windows. you can follow the progress in [the dedicated feature request](https://github.com/flameshot-org/flameshot/issues/2118).

-------

