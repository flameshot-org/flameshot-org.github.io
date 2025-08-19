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


On this page you can find possible solutions for issues on Windows. This page probably needs frequent updates, so if something is outdated, please [report it here](https://github.com/flameshot-org/flameshot-org.github.io/issues/new).

# Keyboard shortcuts

## How to disable Windows Snipping tool when I press PrintScreen

As kindly [explained by one of our users](https://github.com/flameshot-org/flameshot/issues/1551#issuecomment-1232164940), you can disable the built-in snipping tool by going to Windows Settings -> Ease of Access -> Keyboard -> Scroll down to "Print Screen Shortcut" and turn off the "Use the Prtscn button to open screen snipping":

![Windows settings screenshot](/media/content/docs/guide/windows-help/disable-windows-snipping-tool.png)

As some of our users have reported, this does not always solve the issue, because Windows being Windows, it seems you sometimes have to take an extra step to fix this (as [reported](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-1521632771) by [archadallas](https://github.com/archadallas)). This has been explained in [an article on makeuseof.com](https://www.makeuseof.com/windows-11-disable-snipping-tool/#how-to-disable-the-snipping-tool-using-the-registry-editor). If this solves your issue, please up-vote [this](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-1521632771).

## Setting up custom shortcut to start Flameshot

Windows is pretty limited, but there is a way to make windows to start a program with a keybinding. To do this, you have to:
1. create a shortcut file (right-click on Desktop > New > Shortcut)
2. in the "Target" field, add the program you want to run (in this case the path to the `flameshot.exe`)
3. in the "Shortcut key" field, type the keybinding you want (e.g `Ctrl + Alt + p`)

For a more detailed instruction, visit [this article from the Digital Citizen](https://www.digitalcitizen.life/start-windows-apps-keyboard-shortcut/).

### Using PowerToys 

1. Choose remap a shortcut

<img width="1734" height="1213" alt="2025-08-19_10-57" src="https://github.com/user-attachments/assets/dee63f49-3c37-43a9-86db-08d80497f371" />

2. Define your shortcut (e.g. `Ctrl + Alt + s`)
 
<img width="2215" height="1174" alt="2025-08-19_11-00" src="https://github.com/user-attachments/assets/99ba9868-4520-45b5-b1e4-702aa343b118" />

3. In the Action field, Choose `Run Program`
4. In the App field, fill in the path to the `flameshot.exe` file (e.g. `C:\Program Files\Flameshot\bin\flameshot.exe`)
5. In the Args field, fill in `gui`
6. In the If running field, choose `Start another`
7. Choose OK

-------

# CommandLine Interface

For the time being, the Commandline Interface (CLI) is **not** implemented for Windows. you can follow the progress in [the dedicated feature request](https://github.com/flameshot-org/flameshot/issues/2118).

-------

