
Device Installation
===================

In this section we will flash and install our builded images combined with a
chosen rootfs. For this you need a ``hybris-boot.img``, a ``system.img``, a
capable android device and a downloaded rootfs.

Flashing the Halium system on the device
----------------------------------------

.. Note::

   ``BUILDDIR`` is the location of your Halium tree checkout

First you need the halium install tool::

   wget https://raw.githubusercontent.com/Halium/halium-scripts/master/halium-install
   chmod +x halium-install

Then, attach your device in recovery mode (TWRP is recommended). Before you
start flashing it is generally better to create a back-up of your normal system
and to wipe the data partition to be sure there's enough space available. After
doing that you can use the script like that::

   ./halium-install PATH/TO/ROOTFS.tar.gz BUILDDIR/out/target/product/DEVICENAME/system.img

The last step is to boot into fastboot and flash ``hybris-boot.img``::

   fastboot flash boot BUILDDIR/out/target/product/DEVICENAME/hybris-boot.img

Now reboot and start your system! If you encounter any problems, please leave a
comment on the according device-port issue on the
`project management repo <https://github.com/Halium/projectmanagement/issues>`_.
