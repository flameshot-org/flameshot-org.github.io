+++
title = "Install on Windows"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2022-06-01T08:00:00+00:00
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

## Manual installation
- Hosted on [Github](https://github.com/flameshot-org/flameshot/releases). [64-bit 32-bit]

If you want to run Flameshot with the most cutting edge features, you can download a development version from [here](../development-build).


## Using package managers

Windows has few package managers which you can use to easily install and update applications.
Here we list those that have Flameshot in their repository:

### Winget

A quick introduction to WinGet can be found on [Microsoft Documentations](https://docs.microsoft.com/en-us/windows/package-manager/winget/)

```powershell
winget install flameshot
```

### Scoop

Flameshot can be installed using [Scoop extras bucket](https://scoop.sh/#/apps?q=flameshot&s=0&d=1&o=true):

```powershell
scoop bucket add extras
scoop update
scoop install flameshot
```

### Chocolatey

Flameshot is also [available on Chocolatey](https://community.chocolatey.org/packages/flameshot), and can be installed using: 

```powershell
choco install flameshot
```
