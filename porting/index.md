# Porting guide

## Setup your environment

Setting up your environment is necessary before starting the porting process.

### Using Debian (Stretch or newer) or Ubuntu (16.04 LTS or newer)

#### Step 1: Installing required packages

If you are on the `amd64` architecture (commonly referred to as 64 bit), enable the usage of the `i386` architecture:

```
sudo dpkg --add-architecture i386
```

Install the required dependencies:

```
sudo apt install git gnupg flex bison gperf build-essential \
  zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
  libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
  libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \
  python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
  repo liblz4-tool bc
```

**//TODO: Add instructions for installing build tools for other distros as well**

#### Step 2: Create a new directory to download the Halium tree

```
mkdir halium && cd halium
```

If the target device has Android 7.1 or LineageOS 14.1 support, it's recommended to select `halium-7.1`:
```
repo init -u https://github.com/Halium/android -b halium-7.1
```

If your device does not have Android 7.1 or LineageOS 14.1 support but has support for Android 5.1 or CyanogenMod 12.1, select `halium-5.1`:
```
repo init -u https://github.com/Halium/android -b halium-5.1
```

**//TODO: Add notes about halium-5.1 and halium-7.1**

`halium-7.1` is based on LineageOS 14.1
`halium-5.1` is based on CyanogenMod 12.1

#### Step 3: Download the source code

```
repo sync -c
```

Specifying `-c` only downloads one branch, which makes the download a lot smaller since it won't download all of the old branches, this will also result in a much faster sync time.

You can also specify `-j[num]` as it will fetch the files simultaneously. This defaults to 6 consecutive processes but bumping it to 10 makes a big difference on network with high bandwidth.

## Prepare the Android tree

### Put parts together

Now you need to put all the parts for your device together, and since our tree is based on LineageOS for `halium-7.1` or CyanogenMod for `halium-5.1` you can use the device files they provide.

Parts that are needed:
- Device tree
- Kernel source
- Vendor tree (e.g. from [TheMuppets](https://github.com/TheMuppets))

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

### Booting the device

After you built `hybris-boot.img` it is time to test it out.

 1. Connect your device with a USB cable to your desktop.
 2. Start the device in bootloader (aka "fastboot") mode.<br>
 This is usually acomplished by holding some combination of keys on the device for a few seconds. On some devices this is Volume-Down + Power. The Lineage OS wiki is a good resource to check for this.
 3. Change to the directory where the boot images have been created with the command `cout`.
 4. Boot the kernel image with: `fastboot boot hybris-boot.img`

**//TODO: what are we supposed to do with the systemimage? What can we expect from it?**

## Debugging

### Reading kernel logs

To find out what happened during an unsuccessful boot you can check the kernel log files. These can usually be retrieved from `/proc/last_kmsg` after rebooting the device into another, working system. A precondition for this is that you have a system that you can successfully boot, such as TWRP.

 1. Boot your newly built image
 2. Wait for it to fail
 3. Reboot the device into the working system.
 4. Retrieve the kernel log with `adb shell cat /proc/last_kmsg > ~/last_kmsg`
 5. Read `~/last_kmsg` and find out what went wrong

### Debugging via telnet

The hybris-boot image can offer you a telnet interface to access the system on the device even if it does not come up fully. To this end, the usb function of the device will be reconfigured to work as a network interface. While bringing this network interface up, the boot image will write a few debug messages. These debug messages are communicated via a clever hack of resetting the serial number of the usb connection. Once you see that the usb networking and telnet have been set up, you can configure the usb networking on your desktop and then telnet into the system.

The steps in detail are:

 * Execute this command to watch the changes in the usb serial number:<br>
 `while : ; do
    lsusb -v 2>/dev/null \
    | grep -Ee 'iSerial +[0-9]+ +[^ ]'
    done \
  | uniq `
 * Boot your newly built image
 * Watch the output of the lsusb command above. It will put out lines like this:
```
iSerial                 3 01234567
iSerial                 3 Mer Debug setting up (DONE_SWITCH=no)
iSerial                 3 Mer Debug telnet on port 23 on usb0 192.168.2.15 - also running udhcpd
```
  * Determine the name of the usb network device on your desktop:
 `dmesg | tail`. You're looking for a line similar to this:
```
 [ 1234.123456] rndis_host 1-7:1.0 enp0s20f0u7: renamed from usb0
```
 * In this example shown above, `enp0s20f0u7` is the usb network device name. Use this for the USBNETWORK below
 * Check if the usb network device has a MAC address assigned.
```
$ ip address show dev USBNETWORK
6: USBNETWORK: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
```
If it shows the link/ether address `00:00:00:00:00:00` as shown above, you will have to manually assign the MAC address,
```
ip link set USBNETWORK address 02:01:02:03:04:08
```
You can set any MAC address you want, it just needs to be a valid MAC address.
 * Configure usb networking:
```
sudo ip address add 192.168.2.1 dev USBNETWORK
ip address show dev USBNETWORK
sudo ip route  add 192.168.2.15 dev USBNETWORK
ping -c 2 192.168.2.15
```
 * Connect with telnet: `telnet 192.168.2.15`

Now you have terminal access to the system running from initrd.

The `hybris-boot.img` brings up the telnet interface if it detects a problem. Alternatively, you can use the `hybris-recovery.img` image which will always start telnet.


## Porting parts

* [Debug android userspace](debug-android-userspace.md)
* [graphics](graphics.md)
* [lights](lights.md)
* [vibrator](vibrator.md)
* [wifi](wifi.md)

## References

The hybris-boot image is based on work from the Sailfish OS and the [Sailfish Hardware Adaptation Development Kit porting guide](https://sailfishos.org/develop/hadk/) contains valuable tips.
