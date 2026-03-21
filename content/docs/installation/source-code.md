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

The compilation requires **Qt version 6.2 or higher**, **GCC 11 or higher** and **CMake 3.22 or higher**.


### Debian/Ubuntu

Compilation Dependencies:

```sh
apt install g++ cmake build-essential qt6-base-dev qt6-tools-dev-tools qt6-svg-dev qt6-tools-dev
```

### Fedora

Compilation Dependencies:

```sh
dnf install gcc-c++ cmake qt6-qtbase-devel qt6-qtsvg-devel qt6-qttools qt6-linguist qt6-qttools-devel kf6-kguiaddons-devel
```

### Arch

Compilation Dependencies:

```sh
pacman -S cmake base-devel git qt6-base qt6-tools kguiaddons
```

### OSX

Compilation Dependencies:

```sh
brew install qt6
brew install cmake
```

--------------------------------------------------------------------------------

## DE/WM dependencies

### Sway

On Arch:

```sh
pacman -S xdg-desktop-portal xdg-desktop-portal-wlr grim
```

--------------------------------------------------------------------------------

## Getting the Source Code

You can get the source code from [our GitHub repository](https://github.com/flameshot-org/flameshot). Either clone the repository or download a ZIP file. We suggest downloading the ZIP file if you want to build on specific version, but if you want to build different commits and versions, using `git` makes it much easier.
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

At this point, you can use Flameshot even _without installing_ it as you have already compiled the code into a binary file.
The file is stored in `src/flameshot` inside the `build/` directory (which you are already there).
So you can just run it directly by `./src/flameshot`.

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
cmake ../ -DQt6_DIR=$(brew --prefix qt6)/lib/cmake/Qt6
```

**NOTE #3:** If you are on Sway or any other place that installing `grim` applies to you, you should add the following flag to the `cmake` before running it:

```
-DUSE_WAYLAND_CLIPBOARD=true
```


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
