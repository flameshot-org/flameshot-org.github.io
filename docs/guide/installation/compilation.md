# Compilation

## Dependencies

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

## Compilation

Compilation:  run `qmake && make` in the main directory.

## Install
Simply use `make install` with privileges.

## Packaging
In order to generate the makefile installing in `/usr` instead of in `/usr/local` you can use the `packaging` option to generate the proper makefile (`qmake CONFIG+=packaging` instead of just `qmake`).

If you want to install in a custom directory you can define the `BASEDIR` variable.

**Example**:
You want to install Flameshot in ~/myBuilds/test. You would execute the following to do so:
`qmake CONFIG+=packaging BASEDIR=~/myBuilds/test && make install`


