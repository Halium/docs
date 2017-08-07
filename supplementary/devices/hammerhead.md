# Nexus 5 aka Hammerhead

This is one of our **reference devices** and is besides the Nexus 7 2013 (flo) one of the best mainlined smartphones out there.

## Status

### Halium

Halium is **working on this device as version 5.1**. You can find the [kernel here](https://github.com/Halium/android_kernel_lge_hammerhead) and the [device files here](https://github.com/Halium/android_device_lge_hammerhead).

### Distributions

| Ubuntu Touch/Ubports | KDE mobile | Cynogenmod  |                LineageOS                 |
| :------------------: | :--------: | :---------: | :--------------------------------------: |
| ubports 15.04 - ota2 |     ?      | 14.1 latest | [14.1](https://wiki.lineageos.org/devices/hammerhead) |

#### Ubports 15.04 (Android 5.1 base)

The Halium sources above are essentially forks from the ubports [device files](https://github.com/ubports/android_device_lge_hammerhead) and [kernel](https://github.com/ubports/android_kernel_lge_hammerhead). Both **UBports and LOS share a common base** which is Cyanogenmod. However the Ubports kernel received some patches from the **backports project** ([backports on github](https://github.com/ubuntu-phonedations/backports) and the official [wiki](https://backports.wiki.kernel.org/index.php/Main_Page)) whereas the LOS kernel has a few more manual commits.

#### LineageOS 14.1

The sources for LOS 14.1 can be found [here](https://github.com/LineageOS/android_device_lge_hammerhead) and their [kernel here](https://github.com/LineageOS/android_kernel_lge_hammerhead). The kernel is based on version 3.4.0 (according to it's Makefile)

### Kernel & Hardware

Main dts is there [root](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/?h=v4.13-rc4)/[arch](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch?h=v4.13-rc4)/[arm](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm?h=v4.13-rc4)/[boot](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot?h=v4.13-rc4)/[dts](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot/dts?h=v4.13-rc4)/[qcom-msm8974-lge-nexus5-hammerhead.dts](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot/dts/qcom-msm8974-lge-nexus5-hammerhead.dts?h=v4.13-rc4), inside the latest mainline kernel (4.13rc4 as of writing) but how far the functionality goes exactly is unknwon. The general support for Nexus 5 landed with 4.9 according to [phoronix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.9-ARM-Pull). 


## Device Specifics

This should be populated with guides how to get into different boot modes and similar.
