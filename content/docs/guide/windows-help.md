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

Since **v14.0**, the Flameshot screenshot shortcut is freely configurable. However, there are some constraints imposed by Microsoft. Even though Flameshot provides the option to register "every" shortcut, you cannot use any shortcut that is already assigned to a Windows feature!

Additionally, a little more configuration is needed to use <kbd>PrtScr</kbd> and <kbd>Win</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd>. If you want to use one of these, please read the following two chapters.

## How to use PrtScr key

Flameshot is able to detect when Windows forces its own screen snipping tool to open when the <kbd>PrtScr</kbd> key is pressed. If so, the following pop-up will appear when you open the Flameshot settings. Pressing "Yes" disables that Windows setting, and after restarting Flameshot, you can take a screenshot with Flameshot by pressing <kbd>PrtScr</kbd> **if Flameshot is running** (consider enabling the Autostart option!). Pressing "No" will hide the pop-up once and when pressing "No, don't ask again" the pop-up won't show up in future (this is saved in `flameshot.ini` option `ignorePrntScrForcesSnipping`).

![Windows forces snipping](/media/content/docs/guide/windows-help/windows_forces_prntscr.png)

To revert to the default Windows behavior, access Windows Settings > Ease of Access > Keyboard. Scroll down to "Print Screen Shortcut" and toggle the "Use the Prtscn button to open screen snipping" button:

![Windows settings screenshot](/media/content/docs/guide/windows-help/disable-windows-snipping-tool.png)

As some of our users have reported, this does not always solve the issue, because Windows being Windows, it seems you sometimes have to take an extra step to fix this (as [reported](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-1521632771) by [archadallas](https://github.com/archadallas)). This has been explained in [an article on makeuseof.com](https://www.makeuseof.com/windows-11-disable-snipping-tool/#how-to-disable-the-snipping-tool-using-the-registry-editor). If this solves your issue, please up-vote [this](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-1521632771).


## How to use Win+Shift+S

Windows hardbound the shortcut <kbd>Win</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd> for taking a screenshot and by default, this is linked to Microsoft's own Snipping Tool. However, Flameshot can be registered as the "MS-Screenclip" application, which allows you to select Flameshot as the default screenshot tool. Once registered, pressing <kbd>Win</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd> will open Flameshot!

Administrative privileges are required **once** for the following! Start Flameshot as an Administrator, open the Settings > Shortcuts, and select "Register Flameshot as MS-SCREENCLIP application" below the Shortcuts table. Once this has been done, you can restart Flameshot with your usual user privileges.

![Register ms-screenclip](/media/content/docs/guide/windows-help/register-ms-screenclip.png)

The last step is to select Flameshot as the default screen clip application. To do this, access Windows Settings > Apps > Default apps > Screenclip, and select Flameshot:

![Windows settings ms-screenclip](/media/content/docs/guide/windows-help/ms-screenclip.png)

### Alternative: Direct registry change

As an alternative to the above, you can register Flameshot as MS-Screenclip application via a registry change. Administrative privileges are required for this! This procedure may be used e.g. by IT administrators in a company, for example, who want to deploy Flameshot on employees' office computers.

**Do NOT DELETE OR MODIFY any existing keys, you have been warned! Modifying the registry is at your own risk!**

Using a text editor, put the following into a `.reg` file, updating the path to Flameshot in the last line according to your installation, and then run the file on the desired computer.

```reg
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Flameshot\Capabilities\URLAssociations]
"ms-screenclip"="Flameshot"

[HKEY_LOCAL_MACHINE\SOFTWARE\RegisteredApplications]
"Flameshot"="SOFTWARE\\Flameshot\\Capabilities"

[HKEY_CLASSES_ROOT\Flameshot\Shell\Open\command]
@="\"C:\\Program Files\\Flameshot\\bin\\flameshot.exe\" gui"
```

Afterwards, select Flameshot as the default screenshot application in Windows Settings > Apps > Default apps > Screenclip, as shown in the previous chapter.

Original proposal can be found on GitHub in [this comment](https://github.com/flameshot-org/flameshot/issues/1341#issuecomment-3536988036).

Reference for protocol associations can be found in the [official Microsoft documentation](https://learn.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767914%28v=vs.85%29).
