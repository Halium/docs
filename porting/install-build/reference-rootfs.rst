
Halium reference rootfs
=======================

Once you have built the system.img from the android tree, you can download and install the rootfs using the ``halium-install`` script from the `halium-scripts repository <https://github.com/Halium/halium-scripts/>`_.


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

Once in download mode the necessary tool depends on platform:

On Windows, proceed with the Odin flashing tool which takes image files wrapped in tgz format.

On Linux, use the Heimdall flashing tool. Heimdall, when used in command line mode, can handle plain .img files.

On recent devices, only newer versions of Heimdall should be used. Ubuntu´s ppa holds an older version of Heimdall. Do not use this. Instead, build it from source::

    git clone https://github.com/Benjamin-Dobell/Heimdall.git

For building instructions, consult the README.

Note: Often you will find instructions on Samsung ROMs saying that you need to obtain a PIT file before flashing a device. This is not required and could in fact soft-brick your device. The PIT file is the partition table and is only required when repartitioning. This is normally not necessary and using downloaded PIT files is risky.

Heimdall will always reboot by default after flashing. Using the --no-reboot option will leave the connection in a strange state. Therefore, after flashing a .img file it is not possible to immediately push a second one. Also, Heimdall is incapable of rebooting directly into recovery mode.

The command for flashing is::

    heimdall flash --BOOT hybris-boot.img

Install rootfs and system.img
-----------------------------

* Download the halium reference rootfs from `bshah's personal server <http://bshah.in/halium/halium-rootfs-20170630-151006.tar.gz>`_.
* Get the halium-install script from the `JBB's repository <https://gitlab.com/JBBgameich/halium-install/>`_.
* Bring the device into recovery mode and run::

    ./halium-install -p halium <path to rootfs tarball> <path to android system.img>

If you have trouble getting this to work, use the ``-v`` option to get verbose output.

Debugging
---------

Now that you have this installed, move on to :doc:`../debug-build/index` to test your port's functionality.
