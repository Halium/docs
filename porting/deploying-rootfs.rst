
Deploying the rootfs and system.img
===================================

Once you have built the system.img from the android tree, you can download and install the rootfs using the ``halium-install`` script in a `halium-scripts repository <https://github.com/Halium/halium-scripts/>`_.

Currently latest rootfs is available at, bshah's personal server: `Link <http://bshah.in/halium/halium-rootfs-20170630-151006.tar.gz>`_

You can use the halium-install script as below, when device is connected in recovery mode

.. code-block:: guess

   halium-install <path to rootfs tarball> <path to android system.img>

This will do the following,


* Convert the rootfs tarball into ext2 rootfs.img
* Convert system.img into the ext4 mountable image from android sparse image.
* Push the both images to /data partition
