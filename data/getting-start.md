## Installation
There are packages available for a few distros:
- [Arch](https://www.archlinux.org/packages/community/x86_64/flameshot/)
  + Snapshot also available via AUR: [flameshot-git](https://aur.archlinux.org/packages/flameshot-git).
- [Debian 10+](https://tracker.debian.org/pkg/flameshot): `apt install flameshot`
- [Ubuntu 18.04+](https://launchpad.net/ubuntu/+source/flameshot): `apt install flameshot`
- Fedora: `dnf install flameshot`
- [openSUSE](https://software.opensuse.org/package/flameshot)
- [Void Linux](https://github.com/voidlinux/void-packages/tree/master/srcpkgs/flameshot): `xbps-install flameshot`
- [Docker](https://github.com/ManuelLR/docker-flameshot)

In addition, we also have continuous integration, it currently provides the following package:
- Debian8
- Debian9
- Ubuntu16.04
- Ubuntu17.10
- Fedora26
- Fedora27
- AppImage

Check the [Download](/download) for more information.

## Compilation
The compilation requires **Qt version 5.3 or higher** and **GCC 4.9.2 or higher**.

### Debian/Ubuntu
Compilation Dependencies:
````
apt install git g++ build-essential qt5-qmake qt5-default qttools5-dev-tools
````

Compilation: run `qmake && make` in the main directory.

### Fedora
Compilation Dependencies:
````
dnf install qt5-devel gcc-c++ git qt5-qtbase-devel qt5-linguist
````

Compilation:  run `qmake-qt5 && make` in the main directory.

### Arch
Compilation Dependencies:
````
pacman -S git qt5-base base-devel qt5-tools
````

Compilation:  run `qmake && make` in the main directory.

### Install
Simply use `make install` with privileges.

## Packaging
In order to generate the makefile installing in `/usr` instead of in `/usr/local` you can use the `packaging` option to generate the proper makefile (`qmake CONFIG+=packaging` instead of just `qmake`).

If you want to install in a custom directory you can define the `BASEDIR` variable.

**Example**:
You want to install Flameshot in ~/myBuilds/test. You would execute the following to do so:
`qmake CONFIG+=packaging BASEDIR=~/myBuilds/test && make install`

### Runtime Dependencies
**Debian**:
````
libqt5dbus5, libqt5network5, libqt5core5a, libqt5widgets5, libqt5gui5
````
Optional:
```
openssl, ca-certificates
```

**Fedora**:
````
qt5-qtbase
````
Optional:
```
openssl, ca-certificates
```

**Arch**:
````
qt5-base
````
Optional:
```
openssl, ca-certificates
```