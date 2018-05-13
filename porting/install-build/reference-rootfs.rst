
Halium reference rootfs
=======================

Once you have built the system.img from the android tree, you can download and install the rootfs using the ``halium-install`` script from the `halium-scripts repository <https://github.com/Halium/halium-scripts/>`.


Install hybris-boot.img 
-----------------------

First, boot your device into its bootloader. This is normally done by holding Power+Volume Down, but it can be different on each device.

Next, simply execute the following command::

    fastboot flash boot [path/to/]hybris-boot.img

If you're in BUILDDIR, ``hybris-boot.img`` will be located at ``out/target/product/[codename]/hybris-boot.img``.


Install hybris-boot.img on Samsung devices
------------------------------------------

Samsung devices cannot be flashed using fastboot. Instead, the device needs to be brought into "Download Mode". This can be achieved in two ways:

1. By manually by pressing Vol-Down, Home and Power button until the green warning text appears. Then press Vol-Up as instructed.
2. By issuing the command::

    adb reboot download

This mode can only be used together with Odin on Windows or Heimdall on Linux. Neither are official tools, but they are commonly used and they work. While Odin requires all image files to be wrapped in tgz files, Heimdall (in command line mode) will be happy with plain .img files.

On recent devices, only newer versions of the software should be used. Ubuntu´s ppa holds an older version of Heimdall. Do not use this. Instead, build it from source::

    git clone https://github.com/Benjamin-Dobell/Heimdall.git

For building instructions, consult the README.

Note: Often you will find instructions on Samsung ROMs saying that you need to obtain a PIT file before flashing a device. This is not required and could in fact soft-brick your device. (The PIT file is the partition table and is only required when repartitioning. This is normally not necessary and using downloaded PIT files is risky.)

Heimdall will always reboot by default after flashing. Using the --no-reboot option will leave the connection in a strange state. Therefore, after flashing a .img file it is not possible to immediately push a second one. Also, Heimdall is incapable of rebooting directly into recovery mode.

The command for flashing is::

    heimdall flash --BOOT hybris-boot.img
    

Install rootfs and system.img
-----------------------------

Currently the latest rootfs is available at bshah's personal server: `Link <http://bshah.in/halium/halium-rootfs-20170630-151006.tar.gz>`

You can use the halium-install script as below, when device is connected in recovery mode::

   halium-install <path to rootfs tarball> <path to android system.img>

This will do the following: 

* Convert the rootfs tarball into ext2 rootfs.img
* Convert system.img into the ext4 mountable image from android sparse image.
* Push the both images to /data partition

Debugging
---------

Now that you have this installed, move on to :doc:`../debug-build/index` to test your port's functionality.
