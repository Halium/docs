# Porting guide

## Setup your environment

Setting up your environment is necessary before starting porting to any device

## Using Ubuntu

### Step 1, Install building tools

```
sudo apt-get install git gnupg flex bison gperf build-essential \
  zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
  libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
  libgl1-mesa-dev g++-multilib mingw32 tofrodos \
  python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
  g++-4.8-multilib
```

TODO: Add instructions for installing building tools for other distros as well

### Step 2, Download and install the latest repo version

```
mkdir ~/bin
PATH=~/bin:$PATH
cd ~/bin
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

### Step 3, Create a new directory to download the halium tree

```
mkdir phablet
repo init -u https://github.com/Halium/android -b halium-5.1
```

## Prepare the android tree

### Put parts together

Now you need to put all the parts for your device togheter, and since our tree is based on Cyanogenmod you can use the device files they provide. 

Parts that is needed:
- device
- vendor
- kernel

You may check the "cm.dependencies" that is included in every cyanogenmod device repo.

### Modify the kernel configuration

Halium uses the systemd as a init system which requires various kernel config options to be enabled

To check which config options needs to be enabled we use mer-kernel-check utility provided by hybris-boot

```
git clone https://github.com/mer-hybris/mer-kernel-check
cd mer-kernel-check
./mer-kernel-check <path to kernel configuration>
```

### Include device in fixup-mountpoints script if not already

First check if your device is already included in the `hybris-boot/fixup-mountpoints` script.

If not then, you will need to add a code similar to [following](https://github.com/Halium/hybris-boot/blob/master/fixup-mountpoints#L198) in the `fixup-mountpoints` script

To figure out the actual device node for the block device you can use following command

```
readlink -f  /dev/block/platform/msm_sdcc.1/by-name/<blocdevicename>
```


## Building

### Initalize

First we need to Initialize the environment using the envsetup.sh tool:

```
. build/envsetup.sh
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

Now we need to choose the target to build using the lunch command;

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

Here you need to choose your device cm[your device]-userdebug, example if you were to build the oneplus one you would choose cm_bacon-userdebug or 9.

### Building the system.img and hybris-boot.img

To build the system.img and hybris-boot.img, required to run halium reference rootfs use the following commands

```
mka hybris-boot
mka systemimage
```

Once you have hybris-boot.img and system.img built successfully you can move to testing this on your device.

TODO: add testing instructions in this file
