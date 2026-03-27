+++
title = "Install on Linux"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2025-01-30T14:50:24+02:00
draft = false
weight = 1
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'How to install Flameshot on Linux systems.'
toc = true
top = true
+++


# Installation on Linux

## Distro-Specific

There are packages available for different distros:

- **[Arch](https://www.archlinux.org/packages/community/x86_64/flameshot/):** `pacman --sync flameshot`
    - Official AUR: [flameshot-git](https://aur.archlinux.org/packages/flameshot-git).

- **[Debian 10+](https://tracker.debian.org/pkg/flameshot):** `apt install flameshot`

- **[Ubuntu 18.04+](https://launchpad.net/ubuntu/+source/flameshot):** `apt install flameshot`

- **[Fedora](https://src.fedoraproject.org/rpms/flameshot):** `dnf install flameshot`

- **[NixOS](https://search.nixos.org/packages?query=flameshot):** `nix-env --install --attr nixos.flameshot`

- **[Guix](https://packages.guix.gnu.org/packages/flameshot/):** `guix install flameshot`

- **[openSUSE](https://software.opensuse.org/package/flameshot):** `zypper install flameshot`

- **[Void Linux](https://github.com/voidlinux/void-packages/tree/master/srcpkgs/flameshot):** `xbps-install flameshot`

- **[Solus](https://dev.getsol.us/source/flameshot/):** `eopkg install flameshot`



If you want to run Flameshot with the most cutting edge features, you can
download a development version from [here](../development-build) or use AUR if you are on an [Arch-based distro](https://wiki.archlinux.org/title/Arch-based_distributions).


**Important things to Know:**

1. Other than AUR (Arch User Repository) that is officially maintained by Flameshot developers, all packages listed above are maintained by the respective Linux distribution. Therefore, if the version is very old or you have problems installing Flameshot from the commands above, please directly contact the distribution.
2. In rolling-release distros (e.g Arch, Solus), you can expect to get the recent version of Flameshot within the first few days of release, but in nonrolling-release distros (e.g Ubuntu, Debian, Fedora) you will most probably stay a few versions behind, especially if your Linux release version is old (check [here](https://repology.org/metapackage/flameshot/versions)). In these cases you might want to either go for the packages we provide on [Flameshot release page](https://github.com/flameshot-org/flameshot/releases) or go with distro-agnostic solutions which are explained [here](#distro-agnostic).


In addition, we also have continuous integration, it currently provides the following packages which can be accessed via our [GitHub release page](https://github.com/flameshot-org/flameshot/releases):

- Debian10 (buster)
- Ubuntu18.04 (bionic)
- Ubuntu20.04 (focal)
- Fedora31
- Fedora32
- OpenSUSE Leap 15.2

General packages (AppImage, snap, and Flatpak): they can run on common Linux-based operating systems, such as RHEL, CentOS, openSUSE, SLED, Ubuntu, Fedora, Debian and derivatives.

<details>
  <summary>Expand this section to see what distros are using an up to date version of Flameshot</summary>
  <a href="https://repology.org/metapackage/flameshot/versions">
    <img src="https://repology.org/badge/vertical-allrepos/flameshot.svg" alt="Packaging status">
  </a>
</details>


-------------------------------------------------

## Distro-Agnostic

### AppImage

You can always use the AppImage as it is distro agnostic:

1. Navigate to the folder you would like to store the software (the following is a suggestion):

```sh
mkdir --parents ~/Applications/Flameshot
cd ~/Applications/Flameshot
```

2. Delete older versions of Flameshot AppImage:

```sh
rm Flameshot-*x86_64.AppImage
```

3. Download the latest AppImage

   3.1. Get it from [Release page](https://github.com/flameshot-org/flameshot/releases/latest), OR

   3.2. Use the following to automatically download the latest.

    ```sh
    curl --remote-name \
        --remote-header-name \
        --location $(curl -s https://api.github.com/repos/flameshot-org/flameshot/releases/latest \
                    | grep -Po 'https://github.com/flameshot-org/flameshot/releases/download/[^}]*\.AppImage' \
                    | uniq)
    ```

4. Set it to executable:

```sh
chmod +x Flameshot-*.x86_64.AppImage
```

5. Now you have the Flameshot ready and you can run the software:

```sh
./Flameshot-*.x86_64.AppImage
```

This will create an icon in your system tray area (usually in the bottom-right or top-right of the screen). 

6. Now, you can launch the application. You can either:

    6.1. Click on the tray icon and select "Take screenshot"

    6.2. Open terminal and use the following to run the application:

    ```sh
    ./Flameshot-*.x86_64.AppImage gui
    ```
7. You may also add a symlink to the AppImage executable in your PATH. This way you can just run `flameshot` in your terminal and it will automatically run the AppImage. For example:

```sh
ln --symbolic ~/Applications/Flameshot/Flameshot-11.0.0.x86_64.AppImage ~/.local/bin/flameshot

# and now you can simply run
flameshot
```

### Snap

Flameshot is not currently on snap, but when it gets available, you can install Flameshot through:

```sh
snap install flameshot
```

To update the snap applications on your computer, you should run `snap refresh`.


### Flatpak  <img src="https://img.shields.io/flathub/downloads/org.flameshot.Flameshot">

Flameshot is not currently on Flathub, but it will be there soon and the information here will be updated accordingly. For now you can install the Flatpak from the github release:

```sh
flatpak install flathub org.flameshot.Flameshot
```

Alternatively you can install from the github using Flatpak if you want a specific version. For example for getting the version 0.9.0:

```sh
flatpak install https://github.com/flameshot-org/flameshot/releases/download/v0.9.0/org.flameshot.Flameshot-0.9.0.x86_64.flatpak
```

And for running it you should do

```sh
flatpak run org.flameshot.Flameshot
```

To update the flatpaks you can use `flatpak update`.

You may also add a symlink to the Flatpak command in your PATH. For example:

```sh
ln --symbolic /var/lib/flatpak/exports/bin/org.flameshot.Flameshot ~/.local/bin/flameshot
```

This can help when creating custom keyboard shortcuts.


### Docker  <img src="https://img.shields.io/docker/pulls/manuellr/flameshot">  <img src="https://img.shields.io/docker/image-size/manuellr/flameshot?sort=date">

There is also a docker image available for those who want it (**not** maintained by Flameshot maintainers):

<https://github.com/ManuelLR/docker-flameshot>

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
