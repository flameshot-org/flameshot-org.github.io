+++
title = "Install on Windows"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2023-06-28T08:00:00+00:00
draft = false
weight = 3
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'How to install Flameshot on Windows.'
toc = true
top = true
+++


# Installation on Windows

## Stable version

### Using package managers

Windows has few package managers which you can use to easily install and update applications.
Here we list those that have Flameshot in their repository:

#### Winget

A quick introduction to WinGet can be found on [Microsoft Documentations](https://docs.microsoft.com/en-us/windows/package-manager/winget/)

```powershell
winget install flameshot
```

#### Scoop

Flameshot can be installed using [Scoop extras bucket](https://scoop.sh/#/apps?q=flameshot&s=0&d=1&o=true):

```powershell
scoop bucket add extras
scoop update
scoop install flameshot
```

#### Chocolatey

Flameshot is also [available on Chocolatey](https://community.chocolatey.org/packages/flameshot), and can be installed using:

```powershell
choco install flameshot
```

-------

### Manual installation

If you want to manually download and install the Windows version, you have to follow these steps:
1. Go to [the latest release on out Github repo](https://github.com/flameshot-org/flameshot/releases/latest)
   ![](/media/content/docs/installation/installation-windows/2023-06-28_13-45_go_to_latest_release.png)
2. Scroll down to find the "Assets" as shown in the picture below (it might be collapsed, so click on the triangle on the left side to open it)
   ![](/media/content/docs/installation/installation-windows/2023-06-28_13-46_go_to_assets.png)
3. Find the Windows files. They have `win64` in their names. The one that ends with `.msi` is the one that you can install, and the one that ends with `.zip` contains the portable that does not need installation. Portable is good for situations where you do not have administrative access to install software on that computer.
   ![](/media/content/docs/installation/installation-windows/2023-06-28_13-47_find_windows_files.png)

-------

## Development build (a.k.a nightly builds)

If you want to run Flameshot with the most cutting edge features, you can download a development version from [here](../development-build).

