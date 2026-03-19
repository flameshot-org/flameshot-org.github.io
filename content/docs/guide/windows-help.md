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

![PowerToys Keyboard Shortcuts](/media/content/docs/guide/windows-help/PowerToys-KeyboardShortcuts.png)

2. Define your shortcut (e.g. `Ctrl + Alt + s`)

![PowerToys Keyboard Shortcuts Configuration](/media/content/docs/guide/windows-help/PowerToys-KeyboardShortcuts-Configuration.png)

3. In the Action field, Choose `Send Key/Shortcut`
4. Choose `Print Screen`
5. Choose OK
## Overriding Windows default shortcut
**Do NOT DELETE any key or modify any existing ones, you have been warned! Play around in the registry at your own risk!**  
If you want to override <kbd>Win</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd> to take a screenshot using Flameshot directly instead of the default app (Snipping Tool), follow one of the two methods below.  
### Automatic
Put the following in a `.reg` file using any text editor and run it. Update Flameshot's path in the last line if you installed it elsewhere.
```reg
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Flameshot\Capabilities\URLAssociations]
"ms-screenclip"="Flameshot"

[HKEY_LOCAL_MACHINE\SOFTWARE\RegisteredApplications]
"Flameshot"="SOFTWARE\\Flameshot\\Capabilities"

[HKEY_CLASSES_ROOT\Flameshot\Shell\Open\command]
@="\"C:\\Program Files\\Flameshot\\bin\\flameshot.exe\" gui"
```

Original proposal can be found on GitHub in [this comment](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-3536988036).
### Manual
Note: In steps 1-5, you can replace `Flameshot` in the names, values, and paths with any name of your choosing as long as the change is consistently applied.
1. Create this path in Windows Registry:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Flameshot\Capabilities\URLAssociations
```
2. Create a new "String Value" there with the following data:  
	Name: `ms-screenclip`  
	Value: `Flameshot`
3. Go to this path:
```
HKEY_LOCAL_MACHINE\SOFTWARE\RegisteredApplications
```
4. Create a new "String Value" with the name `Flameshot` and value:
```
SOFTWARE\Flameshot\Capabilities
```
5. Then create this path:
```
HKEY_CLASSES_ROOT\Flameshot\Shell\Open\command
```
6. Then set the default key value to where Flameshot is installed, default is:
```
"C:\Program Files\Flameshot\bin\flameshot.exe" gui
```
7. Change the default app by one of the following methods:
   1. Trigger the default hotkey <kbd>Win</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd> and it will show you a prompt to select the default one between Snipping Tool and Flameshot, select Flameshot and choose Always.
   2. Manual instructions:
      1. Open Windows Settings app.
      2. Go to Default Apps.
      3. Scroll down to "Choose defaults by link type" and click it.
      4. Search for "MS-SCREENCLIP" and click on the result.
      5. Flameshot should come up, select it.
      6. Click on "Select default" button.

Reference for protocol associations can be found in the [official Microsoft Documentation](https://learn.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767914%28v=vs.85%29).
