# BQ Aquaris E5 aka Vegeta

The family of Aquaris E5 devices by BQ are all called vegeta +  a special suffix (there is an E5 HD so it's vegetahd for example).

## Status

### Halium

There has been no effort to get Halium onto this device so far.

### Distributions

The following entries are just a placeholder, exactly as this sentence.

|               Distribution               |          Device Specific Files           |                  Kernel                  | What works | What doesn't work |
| :--------------------------------------: | :--------------------------------------: | :--------------------------------------: | :--------: | :---------------: |
| Ubports 15.04 (Android 5.1 base) [device page](https://devices.ubports.com/#/hammerhead) | [android_device_lge_hammerhead](https://github.com/ubports/android_device_lge_hammerhead) | [android_kernel_lge_hammerhead](https://github.com/ubports/android_kernel_lge_hammerhead) based on v3.4.0 |     ?      |         ?         |


### Kernel & Hardware
#### Mainline (4.13rc4 as of writing)
There is a very rudimentary device tree source file inside kernel 4.13rc4 [here](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot/dts/mt6589-aquaris5.dts?h=v4.13-rc4). This still needs a lot of work.

#### Canonical's Ubuntu Touch kernel (3.4.67 based)
This kernel can be found [here](https://github.com/bq/aquaris-E5/tree/aquaris-E5-ubuntu-master)

## Device Specifics

### Guides

This should be populated with guides how to get into different boot modes and similar.

### Developer Info

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

### Usefull Ressources
If anything might be usefull but didn't fit above you can just throw in some links here.