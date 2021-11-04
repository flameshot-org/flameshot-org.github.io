+++
title = "Install on Windows"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
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
- Hosted on [Github](https://github.com). [64-bit](https://github.com/flameshot-org/flameshot/releases), [32-bit](https://github.com/flameshot-org/flameshot/releases)

!!! tip "Tip: Stay ahead of the curve"

    If you want to run Flameshot with the most cutting edge features, you can
    download a development version from [here](/nightly).


## Using package managers

Windows has few package managers which you can use to easily install and update applications. here we list those that have Flameshot in their repository:

### Winget

A quick introduction to WinGet can be found on [Microsoft Documentations](https://docs.microsoft.com/en-us/windows/package-manager/winget/)

```powershell
winget install flameshot
```

### Scoop

Flameshot can be installed using Scoop extras bucket:

```powershell
scoop bucket add extras
scoop update
scoop install flameshot
```

### Chocolatey

Flameshot [has been submitted](https://github.com/chocolatey-community/chocolatey-package-requests/issues/973) to Chocolatey Community Repository and it is waiting for approval. When approved, you can install it via:

```powershell
choco install flameshot
```
