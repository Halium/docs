
Debug Halium
============

.. toctree::
   :maxdepth: 1
   
   dmesg
   early-init
   logging-in
   usbnet
   debug-android-userspace
   graphics
   lights
   vibrator
   wifi

.. _udev-rules:

Add udev rules
--------------

Now that you're logged in, you must create some udev rules to allow some tests to access your hardware. Run the following command, replacing [codename] with your device's codename.::

    cat /var/lib/lxc/android/rootfs/ueventd*.rc|grep ^/dev|sed -e 's/^\/dev\///'|awk '{printf "ACTION==\"add\", KERNEL==\"%s\", OWNER=\"%s\", GROUP=\"%s\", MODE=\"%s\"\n",$1,$3,$4,$2}' | sed -e 's/\r//' >/etc/udev/rules.d/70-[codename].rules

Now, reboot the device.

References
----------

The hybris-boot image is based on work from the Sailfish OS and the `Sailfish Hardware Adaptation Development Kit porting guide <https://sailfishos.org/develop/hadk/>`_ contains valuable tips.
