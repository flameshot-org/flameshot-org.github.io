# Information required for issue reporting
In this page we explain how to properly extract your system information so that you can report it in a [GitHub issue](https://github.com/flameshot-org/flameshot/issues/)
Here we discuss commands to be used in a **GNU/Linux** system. We migh later add similar information for Windows users.

## Flameshot version

```sh
flameshot --version
```
The output would look like:
> Flameshot v0.8.3
> Compiled with Qt 5.15.0

## Display Server Protocol

Basically what we want to know is if you are using X or Wayland. If you want to know what they are and what they do You can read [this article](https://www.secjuice.com/wayland-vs-xorg/).

You can use the following command to determin which one do you use:

```sh
loginctl show-session $(loginctl show-user $(whoami) -p Display --value) -p Type --value
```

## Monitor(s) information

You can get lots of information about the monitors, but we are interested to see only those that are active and in use. You can use `xrandr` command to get the monitor information and here we presenta short version and a long version. The long version is more useful since it also contains information about the orientation of the monitor.

Short format:

```sh
xrandr --listactivemonitors
```
The output would look like:
> Monitors: 3
> 0: +*HDMI-1-1 1920/509x1080/286+1080+0  HDMI-1-1
> 1: +HDMI-0 1080/509x1920/286+3000+0  HDMI-0
> 2: +HDMI-1 1080/509x1920/286+0+80  HDMI-1

Long format:

```sh
xrandr | grep -v " disconnected "
```
The output would look like:
> Screen 0: minimum 8 x 8, current 4080 x 2000, maximum 32767 x 32767
> HDMI-0 connected 1080x1920+3000+0 left (normal left inverted right x axis y axis) 509mm x 286mm
>    1920x1080     60.00*+  59.94    50.00    60.00    50.04
>    1680x1050     59.95
>    1440x900      74.98    59.89
>    1280x1024     75.02    60.02
>    1280x800      59.81
>    1280x720      60.00    59.94    50.00
>    1152x864      75.00
>    1024x768      75.03    70.07    60.00
>    800x600       75.00    72.19    60.32
>    720x576       50.00
>    720x480       59.94
>    640x480       75.00    72.81    59.93    59.94
> HDMI-1 connected 1080x1920+0+80 left (normal left inverted right x axis y axis) 509mm x 286mm
>    1920x1080     60.00*+  59.94    50.00    60.00    50.04
>    1680x1050     59.95
>    1440x900      74.98    59.89
>    1280x1024     75.02    60.02
>    1280x800      59.81
>    1280x720      60.00    59.94    50.00
>    1152x864      75.00
>    1024x768      75.03    70.07    60.00
>    800x600       75.00    72.19    60.32
>    720x576       50.00
>    720x480       59.94
>    640x480       75.00    72.81    59.93    59.94
> HDMI-1-1 connected primary 1920x1080+1080+0 (normal left inverted right x axis y axis) 509mm x 286mm
>    1920x1080     60.00*+
>    1680x1050     59.88
>    1600x900      60.00
>    1280x1024     60.02
>    1440x900      59.90
>    1280x720      60.00
>    1024x768      60.00
>    800x600       60.32
>    640x480       59.94
>    720x400       70.08
>   1920x1080 (0x1bf) 148.500MHz +HSync +VSync
>         h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
>         v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
>   1280x1024 (0x1c8) 108.000MHz +HSync +VSync
>         h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
>         v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
>   1280x720 (0x1ca) 74.250MHz +HSync +VSync
>         h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
>         v: height  720 start  725 end  730 total  750           clock  60.00Hz
>   1024x768 (0x1d0) 65.000MHz -HSync -VSync
>         h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
>         v: height  768 start  771 end  777 total  806           clock  60.00Hz
>   800x600 (0x1d3) 40.000MHz +HSync +VSync
>         h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
>         v: height  600 start  601 end  605 total  628           clock  60.32Hz
>   640x480 (0x1d9) 25.175MHz -HSync -VSync
>         h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
>         v: height  480 start  490 end  492 total  525           clock  59.94Hz

## Graphics card information

For graphics card there are also many ways to get the information but the most two common routes are:

```sh
update-pciids  # you might need to run this with sudo
lspci | grep -i 'vga\|3d\|2d'
```
The output would look like:
> 00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
> 01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] (rev a1)

and

```sh
# in some systems lshw is not installed by default
lshw -class display
```

The output would look like:
> WARNING: you should run this program as super-user.
>   *-display
>        description: VGA compatible controller
>        product: GP106 [GeForce GTX 1060 6GB]
>        vendor: NVIDIA Corporation
>        physical id: 0
>        bus info: pci@0000:01:00.0
>        version: a1
>        width: 64 bits
>        clock: 33MHz
>        capabilities: vga_controller bus_master cap_list rom
>        configuration: driver=nvidia latency=0
>        resources: irq:35 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
>   *-display
>        description: VGA compatible controller
>        product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
>        vendor: Intel Corporation
>        physical id: 2
>        bus info: pci@0000:00:02.0
>        version: 06
>        width: 64 bits
>        clock: 33MHz
>        capabilities: vga_controller bus_master cap_list
>        configuration: driver=i915 latency=0
>        resources: irq:32 memory:d3400000-d37fffff memory:b0000000-bfffffff ioport:f000(size=64)
> WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

## Operating system information

There are many ways to get such information. Perhaps the easiest one is via the following command:

```sh
uname -a
```

which give an out put similar to the following:

> Linux MyComputer 5.8.11-1-MANJARO #1 SMP PREEMPT Wed Sep 23 14:35:40 UTC 2020 x86_64 GNU/Linux