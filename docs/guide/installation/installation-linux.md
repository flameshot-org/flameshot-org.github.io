# Installation on Linux

## Distro-Specific

There are packages available for different distros:

=== "Arch"
    - Package: [flameshot](https://www.archlinux.org/packages/community/x86_64/flameshot/)
    - Install: `pacman -S flameshot`
    - Snapshot also available via AUR: [flameshot-git](https://aur.archlinux.org/packages/flameshot-git).

=== "Debian 10+"
    - Package: [flameshot](https://tracker.debian.org/pkg/flameshot)
    - Install: `apt install flameshot`

=== "Ubuntu 18.04+"
    - Package: [flameshot](https://launchpad.net/ubuntu/+source/flameshot)
    - Install: `apt install flameshot`

=== "Fedora"
    - Package: [flameshot](https://src.fedoraproject.org/rpms/flameshot)
    - Install: `dnf install flameshot`

=== "NixOS"
    - Package: [flameshot](https://search.nixos.org/packages?query=flameshot)
    - Install: `nix-env -iA nixos.flameshot`

=== "openSUSE"
    - Package: [flameshot](https://software.opensuse.org/package/flameshot)

=== "Void Linux"
    - Package: [flameshot](https://github.com/voidlinux/void-packages/tree/master/srcpkgs/flameshot)
    - Install: `xbps-install flameshot`

=== "Solus"
    - Package: [flameshot](https://dev.getsol.us/source/flameshot/)
    - Install: `eopkg install flameshot`


!!! tip "Tip: Stay ahead of the curve"

    If you want to run Flameshot with the most cutting edge features, you can
    download a development version from [here](/nightly).

*Important things to Know:*

1. Other than AUR (Arch user Repository), All packages listed above are maintained by the respective Linux distribution. Therefore, if the version is very old or you have problem installing Flameshot from the commands above, Please directly contact the distribution.
2. In rolling-release distros (e.g Arch, Solus), you can expect to get the recent version of Flameshot withing the first few days of release, but in nonrolling-release distros (e.g Ubuntu, Debian, Fedora) you will most probably few version behind especially if your Linux release version is old (check [here](https://repology.org/metapackage/flameshot/versions)). In these cases you might want to either go for the packages we provide on [Flameshot release page](https://github.com/flameshot-org/flameshot/releases) or go with distro-agnostic solutions which are explained [here](#distro-agnostic).


In addition, we also have continuous integration, it currently provides the following packages which can be accessed via our [Github release page](https://github.com/flameshot-org/flameshot/releases):

- Debian10 (buster)

- Ubuntu18.04 (bionic)

- Ubuntu20.04 (focal)

- Fedora31

- Fedora32

- OpenSUSE Leap 15.2

General packages(AppImage, snap, and Flatpak): they can run on common Linux-based operating systems, such as RHEL, CentOS, openSUSE, SLED, Ubuntu, Fedora, debian and derivatives. 

<details>
  <summary>Expand this section to see what distros are using an up to date version of flameshot</summary>
  <a href="https://repology.org/metapackage/flameshot/versions">
    <img src="https://repology.org/badge/vertical-allrepos/flameshot.svg" alt="Packaging status">
  </a>
</details>


-------------------------------------------------

## Distro-Agnostic

=== "AppImage"

    You can always use the AppImage as it is distro agnostic:

    1. Navigate to the folder you would like to store the software (the following is a suggestion):

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

=== "Snap"

    Flameshot is not currently on snap, but when it gets available, you can install Flameshot through:

    ```sh
    snap install flameshot
    ```

    to update the snap applications on your computer, you should run `snap refresh`.

=== "Flatpak"

    Flameshot is not currently on Flathub, but it will be there soon and the information here will be updated accordingly. For now you can install the Flatpak from the github release:

    ```sh
    flatpak install flathub org.flameshot.Flameshot
    ```

    Alternatively you can install from the github using Flatpak if you want a specific version. For example for getting the version 0.9.0:

    ```sh
    flatpak install https://github.com/flameshot-org/flameshot/releases/download/v0.9.0/org.flameshot.Flameshot-0.9.0.x86_64.flatpak
    ```

    And for runing it you should do

    ```sh
    flatpak run org.flameshot.Flameshot
    ```

    To update the flatpaks you can use `flatpak update`.

=== "Docker"

    There is also a docker image available for those who want (**not** maintained by Flameshot maintainers):

    https://github.com/ManuelLR/docker-flameshot

-------------------------------------------------

## Runtime Dependencies

### Debian

```sh
libqt5dbus5, libqt5network5, libqt5core5a, libqt5widgets5, libqt5gui5
```
Optional:

```sh
openssl, ca-certificates
```

### Fedora
```sh
qt5-qtbase
```

Optional:

```sh
openssl, ca-certificates
```

### Arch

```sh
qt5-base
```
Optional:

```sh
openssl, ca-certificates
```
