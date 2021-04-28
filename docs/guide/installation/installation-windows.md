# Installation on Windows

## Manual installation
- Hosted on [Github](https://github.com). [64-bit](https://github.com/flameshot-org/flameshot/releases), [32-bit](https://github.com/flameshot-org/flameshot/releases)


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
