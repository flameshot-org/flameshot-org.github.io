+++
title = "From Source Code"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2022-06-01T08:00:00+00:00
draft = false
weight = 5
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'Build Flameshot from source.'
toc = true
top = true
+++


## From Source

Alternatively, you can always compile from the source code.


## OS Dependencies

The compilation requires **Qt version 5.3 or higher** and **GCC 4.9.2 or higher**.


### Debian/Ubuntu

Compilation Dependencies:

```sh
apt install g++ cmake extra-cmake-modules build-essential qtbase5-dev qttools5-dev-tools qttools5-dev libqt5dbus5 libqt5network5 libqt5core5a libqt5widgets5 libqt5gui5 libqt5svg5-dev
```

### Fedora

Compilation Dependencies:

```sh
dnf install gcc-c++ cmake qt5-qtbase-devel qt5-linguist qt5-qtsvg-devel
```

### Arch

Compilation Dependencies:

```sh
pacman -S cmake base-devel git qt5-base qt5-tools hicolor-icon-theme qt5-svg
```

### OSX

Compilation Dependencies:

```sh
brew install qt5
brew install cmake
```

--------------------------------------------------------------------------------

## DE/WM dependencies

### Gnome

### KDE

On Fedora:

```sh
dnf install kf5-kguiaddons-devel
```

On Arch:

```sh
pacman -S kguiaddons
```

### Sway

On Arch:

```sh
pacman -S xdg-desktop-portal xdg-desktop-portal-wlr grim
```

--------------------------------------------------------------------------------

## Getting the Source Code

You can get the source code from [our Github repository](https://github.com/flameshot-org/flameshot). Either clone the repository or download a ZIP file. We suggest downloading the ZIP file if you want to build on specific version, but if you want to build different commits and versions, using `git` makes it much easier.
Please note that in this page we explain how to download the [master branch](https://github.com/flameshot-org/flameshot/tree/master), but you can get the source code for every [Pull Request](https://github.com/flameshot-org/flameshot/pulls) and compile them if you like to.

In general we suggest you to create a temporary directory to download the file and do the compiling there:

```sh
# create the folder
mkdir --parents ~/tmp/flameshot_source/

# go inside the new foldr
cd ~/tmp/flameshot_source/
```

To download [the ZIP file from the master branch](https://github.com/flameshot-org/flameshot/archive/refs/heads/master.zip) you can run:

```sh
curl --remote-name https://github.com/flameshot-org/flameshot/archive/refs/heads/master.zip
```

Alternatively, to clone the Git repository:

```sh
git clone https://github.com/flameshot-org/flameshot.git
```

--------------------------------------------------------------------------------

## Compilation

```sh
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local ../
make
```

**NOTE #1:** for macOS you should replace command

```sh
cmake ../
```

**NOTE #2:** you can speed up the compilation by using the `-j` argument for `make` and specify the number of cores you would like to use.
You can read more about the `make` arguments by `man make` in terminal or [clicking here](https://linux.die.net/man/1/make).
For example the following would use all CPU cores except 1:

```sh
make -j$(nproc --ignore 1)
```

to

```sh
cmake ../ -DQt5_DIR=$(brew --prefix qt5)/lib/cmake/Qt5
```

At this point, you can use Flameshot even _without installing_ it as you have already compiled the code into a binary file.
The file is stored in `src/flameshot` inside the `build/` directory (which you are already there).
So you can just run it directly by `./src/flameshot`.

--------------------------------------------------------------------------------

## Install

But to install it, simply run `make install` with privileges.

--------------------------------------------------------------------------------

## Packaging

In order to generate the makefile installing in `/usr` instead of in `/usr/local` you can use the `packaging` option to generate the proper makefile (`cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr` instead of just `cmake`).

If you want to install in a custom directory you can define the `BASEDIR` variable.

**Example**:
You want to install Flameshot in ~/myBuilds/test. You would execute the following to do so:
`cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr BASEDIR=~/myBuilds/test && make install`
