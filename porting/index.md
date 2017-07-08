# Porting guide

## Setup your environment

Setting up your environment is necessary before starting the porting process.

### Using Ubuntu

#### Step 1: Installing required packages

```
sudo apt-get install git gnupg flex bison gperf build-essential \
  zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
  libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
  libgl1-mesa-dev g++-multilib mingw32 tofrodos \
  python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
  g++-4.8-multilib
```

**//TODO: Add instructions for installing building tools for other distros as well**

#### Step 2: Installing Repo

Repo is a tool that makes it easier to work with Git in the context of Android. [More information](https://source.android.com/source/developing)

```
mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

#### Step 3: Create a new directory to download the Halium tree

```
mkdir halium && cd halium
```

If the target device has Android 7.1 or LineageOS 14.1 support, it's recommended to select halium-7.1
```
repo init -u https://github.com/Halium/android -b halium-7.1
```

If your device does not have Android 7.1 or LineageOS 14.1 support but has Android 5.1 or CyanogenMod 12.1 select halium-5.1

```
repo init -u https://github.com/Halium/android -b halium-5.1
```

**//TODO: Add notes about halium-5.1 and halium-7.1**

halium-7.1 is based on LineageOS 14.1
halium-5.1 is based on CyanogenMod 12.1

#### Step 4: Download the source code

```
repo sync -c
```

`-c` this only download one branch, this makes the source a lot smaller since it won't download all old branches, this will also result in a much faster sync time.

`-j[num]` this set projects to fetch simultaneously, this also results in faster sync time, this defaults to 6 but bumping it to 10 makes a big difference on network with high bandwidth.

## Prepare the Android tree

### Put parts together

Now you need to put all the parts for your device together, and since our tree is based on LineageOS for `halium-7.1` or CyanogenMod for `halium-5.1` you can use the device files they provide.

Parts that is needed:
- device tree
- kernel source
- vendor tree (eg from [TheMuppets](https://github.com/TheMuppets))

You might have to check `lineage.dependencies`/`cm.dependencies` that is included in every LineageOS/CyanogenMod device repo for additional repositories.

**//TODO: Include documentation about local_manifests.**

### Modify the kernel configuration

Halium uses the systemd as the init system which requires various kernel config options to be enabled.

To check which config options needs to be enabled we use [mer-kernel-check](https://github.com/mer-hybris/mer-kernel-check) utility provided by mer-hybris.

```
git clone https://github.com/mer-hybris/mer-kernel-check
cd mer-kernel-check
./mer_verify_kernel_config <path to kernel configuration>
```

If you don't know the path to your kernel config run `grep "TARGET_KERNEL_CONFIG" device/<VENDOR>/<CODENAME>/BoardConfig.mk`. It should be in `arch/arm/configs/<CONFIG>` or `arch/arm64/configs/<CONFIG>` depending on the architecture of your device.

### Include your device in fixup-mountpoints script

First check if the codename of your device is already included in the `halium/hybris-boot/fixup-mountpoints` script.

If it's not already included, you will need to add a few lines similar to [following](https://github.com/Halium/hybris-boot/blob/master/fixup-mountpoints#L198-L205) in the `fixup-mountpoints` script for all partitions that are mountable (i.e. have an `fstype` of `ext4`, `vfat`, `f2fs` or others). You can ignore the rest of the partitions.

To figure out the actual device node for the block device you can use following command:

```
readlink -f /dev/block/platform/msm_sdcc.1/by-name/<blockdevicename>
```


## Building

### Initialize

First we need to initialize the environment using the envsetup.sh tool:

```
source build/envsetup.sh
```

This will give you an output that looks like this:
```
including device/samsung/maguro/vendorsetup.sh
including device/samsung/toro/vendorsetup.sh
including device/samsung/tuna/vendorsetup.sh
including device/samsung/manta/vendorsetup.sh
including device/samsung/crespo4g/vendorsetup.sh
including device/samsung/torospr/vendorsetup.sh
including device/generic/armv7-a-neon/vendorsetup.sh
including device/generic/x86/vendorsetup.sh
including device/oneplus/bacon/vendorsetup.sh
including device/lge/hammerhead/vendorsetup.sh
including device/lge/mako/vendorsetup.sh
including device/asus/tilapia/vendorsetup.sh
including device/asus/deb/vendorsetup.sh
including device/asus/flo/vendorsetup.sh
including device/asus/grouper/vendorsetup.sh
```

### Choose you target

Now we need to choose the target to build using the lunch command:

```
lunch
```

The output of this command will look something like this:

```
You're building on Linux

Lunch menu... pick a combo:
 1. aosp_arm64-eng 	 4. aosp_mips-eng 	  7. cm_bacon-eng
 2. aosp_arm-eng 	 5. aosp_x86_64-eng   8. cm_bacon-user
 3. aosp_mips64-eng  6. aosp_x86-eng      9. cm_bacon-userdebug

Which would you like? [aosp_arm-eng]
```

Here you need to choose your device `cm_[your device]-userdebug`, example if you were to build the OnePlus One you would choose `cm_bacon-userdebug` or `9`.

**//TODO: LineageOS recommends the breakfast tool instead of lunch.**

### Building the system.img and hybris-boot.img

To build the `system.img` and `hybris-boot.img` - required for Halium - use the following commands

```
mka hybris-boot
mka systemimage
```

If you use `make` and not `mka` it's recommended to set `-j[num]` to do parallel building, this reduces build time. *NOTE* this is not needed on halium-7.1 since it will calculate parallel building based on CPU performance.

If you are hitting an error with `mka hybris-boot` about the command `mkbootimg` missing, run `mka mkbootimg` and then `mka hybris-boot` again.

Once you have `hybris-boot.img` and `system.img` built successfully you can move to testing this on your device.

**//TODO: add testing instructions in this file**

## Porting parts

* [Debug android userspace](debug-android-userspace.md)
* [graphics](graphics.md)
* [lights](lights.md)
* [vibrator](vibrator.md)
* [wifi](wifi.md)
