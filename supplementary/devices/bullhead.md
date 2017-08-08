# Nexus 5X aka Bullhead

This is supposed to become one of our **reference devices**.

## Status

### Halium

Halium is **being worked on for this device **. You can find the [kernel here](https://github.com/Halium/android_kernel_lge_bullhead) and the [device files here](https://github.com/Halium/android_device_lge_bullhead).

### Distributions

| Ubuntu Touch/Ubports | KDE mobile | Cynogenmod |                LineageOS                 |
| :------------------: | :--------: | :--------: | :--------------------------------------: |
|          ?           |     ?      |     ?      | [14.1](https://wiki.lineageos.org/devices/bullhead) |

#### LineageOS 14.1

The sources for LOS 14.1 can be found [here (device specific files)](https://github.com/LineageOS/android_device_lge_bullhead)  and their [kernel here](https://github.com/LineageOS/android_kernel_lge_bullhead). The kernel is based on version 3.10.73 (according to it's Makefile)

### Kernel & Hardware

There is no device tree source (dts) file in the mainline kernel (4.13rc4 as of writing), neither for the device itself nor for the underlying SoC (MSM8992). The general support for Nexus 5X and Nexus 6 landed with 4.10 according to [phoronix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.10-ARM-Tegra-More). A short slideshow by Jeremy McNicoll about the initial and ongoing mainlining process already happening is [hosted by the linux foundation here](http://events.linuxfoundation.org/sites/events/files/slides/JRM_NEXUS_ELC_2017.pdf).


## Device Specifics

This should be populated with guides how to get into different boot modes and similar.
