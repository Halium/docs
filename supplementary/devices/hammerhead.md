# Nexus 5 aka Hammerhead

This is one of our **reference devices** and is besides the Nexus 7 2013 (flo) one of the best mainlined smartphones out there.

## Status

### Halium

Halium is **working on this device as version 5.1**. You can find the [kernel here](https://github.com/Halium/android_kernel_lge_hammerhead) and the [device files here](https://github.com/Halium/android_device_lge_hammerhead).

### Distributions

|               Distribution               |          Device Specific Files           |                  Kernel                  | What works | What doesn't work |
| :--------------------------------------: | :--------------------------------------: | :--------------------------------------: | :--------: | :---------------: |
| LineageOS 14.1 [device page](https://wiki.lineageos.org/devices/hammerhead) | [android_device_lge_hammerhead](https://github.com/LineageOS/android_device_lge_hammerhead) | [android_kernel_lge_hammerhead](https://github.com/LineageOS/android_kernel_lge_hammerhead) based on v3.4.0 |     ?      |         ?         |
| Ubports 15.04 (Android 5.1 base) [device page](https://devices.ubports.com/#/hammerhead) | [android_device_lge_hammerhead](https://github.com/ubports/android_device_lge_hammerhead) | [android_kernel_lge_hammerhead](https://github.com/ubports/android_kernel_lge_hammerhead) based on v3.4.0 |     ?      |         ?         |


### Kernel & Hardware
#### Mainline (4.13rc4 as of writing)
Main **device tree source (dts) is available** at [qcom-msm8974-lge-nexus5-hammerhead.dts](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot/dts/qcom-msm8974-lge-nexus5-hammerhead.dts?h=v4.13-rc4), inside the latest mainline kernel but how far the functionality goes exactly is unknwon. The general support for Nexus 5 landed with 4.9 according to [phoronix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.9-ARM-Pull). 

#### Cyanogemod based kernels (LOS & UBP)
Both **UBports(UBP) and LOS share a common base** which is Cyanogenmod. However the Ubports kernel received some patches from the **backports project** ([backports on github](https://github.com/ubuntu-phonedations/backports) and the official [wiki](https://backports.wiki.kernel.org/index.php/Main_Page)) whereas the LOS kernel has a few more manual commits.

## Device Specifics

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the LOS device database. For now check the LOS device page linked in the table above.
