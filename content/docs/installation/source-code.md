+++
title = "From Source Code"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
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

Alternatively, you can always compile from the source.


## Dependencies

The compilation requires **Qt version 5.3 or higher** and **GCC 4.9.2 or higher**.


### Debian/Ubuntu

Compilation Dependencies:

```sh
apt install g++ cmake extra-cmake-modules build-essential qt5-default qttools5-dev-tools qttools5-dev libqt5dbus5 libqt5network5 libqt5core5a libqt5widgets5 libqt5gui5 libqt5svg5-dev
```


### Fedora

Compilation Dependencies:

```sh
dnf install gcc-c++ cmake qt5-devel qt5-qtbase-devel qt5-linguist
```


### Arch

Compilation Dependencies:

```sh
pacman -S cmake base-devel git qt5-base qt5-tools
```


### OSX

Compilation Dependencies:

```sh
brew install qt5
brew install cmake
```


## Compilation

```sh
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local ../
make
```

**NOTE:** for macOS you should replace command

```sh
cmake ../
```

to

```sh
cmake ../ -DQt5_DIR=$(brew --prefix qt5)/lib/cmake/Qt5
```

## Install

Simply use `make install` with privileges.

## Packaging

In order to generate the makefile installing in `/usr` instead of in `/usr/local` you can use the `packaging` option to generate the proper makefile (`cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr` instead of just `cmake`).

If you want to install in a custom directory you can define the `BASEDIR` variable.

**Example**:
You want to install Flameshot in ~/myBuilds/test. You would execute the following to do so:
`cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr BASEDIR=~/myBuilds/test && make install`
