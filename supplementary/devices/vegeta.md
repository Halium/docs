# BQ Aquaris E5 aka Vegeta

The family of Aquaris E5 devices by BQ are all called vegeta +  a special suffix (there is an E5 HD so it's vegetahd for example).

## Status

### Halium

Of course we are mainly interested in Halium status. Therefore please state 

* Is someone already working on Halium for this device? If YES: link to repositories of **device specific files** (usually github repos called "android_device_manufacturer_codename") and **device kernel** (usually a repo beginning with "android_kernel_") and name authors if possible (perhaps link to their github profile)
* Is Halium working for this device? If YES: Name the android base version (5.1 or 7.1) and everything you know about the actual status (what's working, which rootfs, ...)

### Distributions

The following entries are just a placeholder, exactly as this sentence.

|               Distribution               |          Device Specific Files           |                  Kernel                  | What works | What doesn't work |
| :--------------------------------------: | :--------------------------------------: | :--------------------------------------: | :--------: | :---------------: |
| LineageOS 14.1 [device page](https://wiki.lineageos.org/devices/hammerhead) | [android_device_lge_hammerhead](https://github.com/LineageOS/android_device_lge_hammerhead) | [android_kernel_lge_hammerhead](https://github.com/LineageOS/android_kernel_lge_hammerhead) based on v3.4.0 |     ?      |         ?         |
| Ubports 15.04 (Android 5.1 base) [device page](https://devices.ubports.com/#/hammerhead) | [android_device_lge_hammerhead](https://github.com/ubports/android_device_lge_hammerhead) | [android_kernel_lge_hammerhead](https://github.com/ubports/android_kernel_lge_hammerhead) based on v3.4.0 |     ?      |         ?         |


### Kernel & Hardware
#### Mainline (4.13rc4 as of writing)
There is a very rudimentary device tree source file inside kernel 4.13rc4 [here](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot/dts/mt6589-aquaris5.dts?h=v4.13-rc4). This still needs a lot of work.

#### Cyanogemod based kernels (LOS & UBP)
If other kernels exist, just make up headlines with a name that describe the origin (Cyanogemod, LineageOS, UBports, Canonical, ...) and which is the underlying mainline version. Afterwards describe what's been improved or altered and if possible why or what is still missing.

## Device Specifics

### Guides

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the [LOS device database](https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices).

### Developer Info

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

### Usefull Ressources
If anything might be usefull but didn't fit above you can just throw in some links here.