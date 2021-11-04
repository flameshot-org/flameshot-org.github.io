+++
title = "Issue Reporting"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2021-05-01T08:00:00+00:00
draft = false
weight = 10
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'Reporting your issues with Flameshot.'
toc = true
top = false
+++


In this page we explain how to properly extract your system information so that you can report it in a GitHub issue Here we discuss commands to be used in a **GNU/Linux system**. We might later add similar information for Windows users.

## Flameshot version

```bash
flameshot --version
```

The output would look like:

```bash
Flameshot v0.8.3
Compiled with Qt 5.15.0
```

## Quick collection of the system information

Providing the output of this command would usually be enough for a bug report. For much more detailed method, move on to the next section. This method uses a tool that is most probably installed on your computer names ``inxi`` and it can quickly collect the graphical information we need. We are only interested in the "systemS" and "Graphics" section:

```bash
inxi --width 80 --system --graphics
```

which should produce an output similar to the following:

```bash
System:
  Host: MyBox Kernel: 5.10.15-1-MANJARO x86_64 bits: 64
  Desktop: KDE Plasma 5.20.5 Distro: Manjaro Linux
Graphics:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics
  driver: i915 v: kernel
  Device-2: NVIDIA GP106 [GeForce GTX 1060 6GB] driver: nvidia v: 460.39
  Display: x11 server: X.Org 1.20.10 driver: loaded: modesetting,nvidia
  unloaded: nouveau resolution: 1: 1080x1920~60Hz 2: 1080x1920~60Hz
  3: 1920x1080~60Hz
  OpenGL: renderer: GeForce GTX 1060 6GB/PCIe/SSE2 v: 4.6.0 NVIDIA 460.39
```

## Detailed methods

### Display Server Protocol

Basically what we want to know is if you are using X or Wayland. If you want to know what they are and what they do You can read [this article](https://www.secjuice.com/wayland-vs-xorg/).

You can use the following command to determine which one do you use:

```bash
loginctl show-session $(loginctl show-user $(whoami) -p Display --value) -p Type --value
```

### Monitor(s) information

You can get lots of information about the monitors, but we are interested to see only those that are active and in use. You can use ``xrandr`` command to get the monitor information and here we presenta short version and a long version. The long version is more useful since it also contains information about the orientation of the monitor.

Short format:

```bash
xrandr --listactivemonitors
```

The output would look like:

```bash
Monitors: 3
0: +*HDMI-1-1 1920/509x1080/286+1080+0  HDMI-1-1
1: +HDMI-0 1080/509x1920/286+3000+0  HDMI-0
2: +HDMI-1 1080/509x1920/286+0+80  HDMI-1
```

Long format:

```bash
xrandr | grep -v " disconnected "
```

The output would look like:

```bash
Screen 0: minimum 8 x 8, current 4080 x 2000, maximum 32767 x 32767
HDMI-0 connected 1080x1920+3000+0 left (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  59.94    50.00    60.00    50.04
   1680x1050     59.95
   1440x900      74.98    59.89
   1280x1024     75.02    60.02
   1280x800      59.81
   1280x720      60.00    59.94    50.00
   1152x864      75.00
   1024x768      75.03    70.07    60.00
   800x600       75.00    72.19    60.32
   720x576       50.00
   720x480       59.94
   640x480       75.00    72.81    59.93    59.94
HDMI-1 connected 1080x1920+0+80 left (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  59.94    50.00    60.00    50.04
   1680x1050     59.95
   1440x900      74.98    59.89
   1280x1024     75.02    60.02
   1280x800      59.81
   1280x720      60.00    59.94    50.00
   1152x864      75.00
   1024x768      75.03    70.07    60.00
   800x600       75.00    72.19    60.32
   720x576       50.00
   720x480       59.94
   640x480       75.00    72.81    59.93    59.94
HDMI-1-1 connected primary 1920x1080+1080+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+
   1680x1050     59.88
   1600x900      60.00
   1280x1024     60.02
   1440x900      59.90
   1280x720      60.00
   1024x768      60.00
   800x600       60.32
   640x480       59.94
   720x400       70.08
  1920x1080 (0x1bf) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1280x1024 (0x1c8) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x1ca) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1024x768 (0x1d0) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x1d3) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x1d9) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
```

### Graphics card information

For graphics card there are also many ways to get the information but the most two common routes are:
