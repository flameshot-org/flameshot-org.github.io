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
- [Solus](https://dev.getsol.us/source/flameshot/): `eopkg install flameshot`

In addition, we also have continuous integration, it currently provides the following package:
- Debian8 (jessie)
- Debian9 (stretch)
- Ubuntu16.04 (xenial)
- Ubuntu17.10 (artful)
- Fedora26
- Fedora27

General packages(AppImage, snap, and Flatpak): they can run on common Linux-based operating systems, such as RHEL, CentOS, openSUSE, SLED, Ubuntu, Fedora, debian and derivatives. 


- AppImage

You can always use the AppImage as it is distro agnostic:

1. Naviaget to the folder you would like to store the software (the following is a suggestion):

```sh
mkdir -p ~/Applications/Flameshot
cd ~/Applications/Flameshot
```

2. Delete older versions of Flameshot AppImage:

```sh
rm Flameshot-*-x86_64.AppImage
```

3. Download the latest AppImage
   2.1. Get it from [Release page](https://github.com/flameshot-org/flameshot/releases/latest)
   OR
   2.2. use the following to automatically download the latest.

 ```sh
curl -O -J -L $(curl -s https://api.github.com/repos/flameshot-org/flameshot/releases/latest \
                | grep -Po 'https://github.com/flameshot-org/flameshot/releases/download/[^}]*\.AppImage' \
                | uniq)
 ```

4. Set it to executable:

```sh
chmod +x Flameshot-*-x86_64.AppImage
```

5. Now you have the Flameshot ready and you can run the software:

```sh
./Flameshot-*-x86_64.AppImage
```

This will create an icon in your system tray area. (usually in the bottom-right ot top-right of the screen). You can now either:

6.1 click on the tray icon and select "Take screenshot"

6.2 open terminal and use the following to run the application:

```sh
./Flameshot-*-x86_64.AppImage gui
```


- Snap

Flameshot is not currently on snap, but when it gets available, you can install Flameshot through:

```sh
snap install flameshot
```

to update the snap applications on your computer, you should run `snap refresh`.


- Flatpak

Flameshot is not currently on Flathub, but it will be there soon and the information here will be updated accordingly. For now you can install the Flatpak from the github release:

```sh
flatpak install https://github.com/flameshot-org/flameshot/releases/download/v0.8.0/org.flameshot.flameshot_0.8.0_x86_64.flatpak
```

and for runing it you should do

```sh
flatpak run org.flameshot.flameshot
```

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

## Issue reporting

To report a bug or suggest a new feature, you can go to [GitHub issues page](github.com/flameshot-org/flameshot/issues) and use the searchbox in the middle of the page to see if anyone else have already posted something similar. Sometimes you will find a quick solution just by reading the threads. In case of feature request, if you find someone with similar idea, just give that a thumbs-up to increase its priority/importance.

In case you didn't find similar issue, create a new issue and explain in details what the issue is. If you can, add pictures or video recordings to clarify the situation. For bug reports, make sure to also visit [issue reporting page](/issue-reporting) in which we have explained how to get the information we need in each bug report.