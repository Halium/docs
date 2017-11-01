
Halium reference rootfs
=======================

Once you have built the system.img from the android tree, you can download and install the rootfs using the ``halium-install`` script from the `halium-scripts repository <https://github.com/Halium/halium-scripts/>`_.


Install hybris-boot.img
-----------------------

First, boot your device into its bootloader. This is normally done by holding Power+Volume Down, but it can be different on each device.

Next, simply execute the following command::

    fastboot flash boot [path/to/]hybris-boot.img

If you're in BUILDDIR, ``hybris-boot.img`` will be located at ``out/target/product/[codename]/hybris-boot.img``.


Install rootfs and system.img
-----------------------------

Currently latest rootfs is available at bshah's personal server: `Link <http://bshah.in/halium/halium-rootfs-20170630-151006.tar.gz>`_

You can use the halium-install script as below, when device is connected in recovery mode::

   halium-install <path to rootfs tarball> <path to android system.img>

This will do the following:

* Convert the rootfs tarball into ext2 rootfs.img
* Convert system.img into the ext4 mountable image from android sparse image.
* Push the both images to /data partition

Debugging
---------

Now that you have this installed, move on to :doc:`../debug-build/index` to test your port's functionality.
