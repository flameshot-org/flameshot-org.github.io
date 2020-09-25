In this page we explain how to install AppImage, snap, or Flatpak.


## AppImage
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


## Snap

Flameshot is not currently on snap, but when it gets available, you can install Flameshot through:

```sh
snap install flameshot
```

to update the snap applications on your computer, you should run `snap refresh`.


## Flatpak

Flameshot is not currently on Flathub, but it will be there soon and the information here will be updated accordingly. For now you can install the Flatpak from the github release:

```sh
flatpak install https://github.com/flameshot-org/flameshot/releases/download/v0.8.0/org.flameshot.flameshot_0.8.0_x86_64.flatpak
```

and for runing it you should do

```sh
flatpak run org.flameshot.flameshot
```
