
Yuga - Sony Xperia Z
====================

There exists basic mainline kernel support added by Sony. This possibly could
become a reference device.

Status
------

Halium
^^^^^^

There is a **working Halium 7.1** port made by `LNJ <https://github.com/LNJ2>`_
and here is the according `Halium project management issue <https://github.com/Halium/projectmanagement/issues/19>`_.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `Yuga on LineageOS Wiki <https://wiki.lineageos.org/devices/yuga/>`_
     - `LineageOS/android_device_sony_yuga <https://github.com/lineageos/android_device_sony_yuga>`_
     - `LineageOS/android_kernel_sony_apq8064 <https://github.com/lineageos/android_kernel_sony_apq8064>`_ based on v3.4.113
     - everything
     -


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (v4.15-rc9 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The kernel will start and there is already UART and USB debugging implemented
for this device. There also has been worked on riva, which is used for
connectivity like WiFi, Bluetooth and FM, but there is no documentation of what
really works.

LineageOS kernel (v3.4.113)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

This is just the original Sony kernel with some security fixes, updates and back
ports. Unfortunately the LTS has ended, so 3.4.113 is the last version.


Device Specifics
----------------

Guides
^^^^^^

You can always get into fastboot by holding the power button and the volume up
button until the device vibrates three times, then only press the volume up
button and you'll get into fastboot. If you use a LineageOS/CyanogenMod boot image
you can also press volume up or down, when the LED turns pink on startup.

I always had to flash TWRP to the boot partition to get into the recovery again.
Currently I don't know if there is any way to get into the recovery in a simpler
way.


Developer Info
^^^^^^^^^^^^^^

There's no strange behaviour, except the way to get into fastboot or recovery.

Useful Resources
^^^^^^^^^^^^^^^^

`TWRP for yuga <https://twrp.me/sony/sonyxperiaz.html>`_ (only up to v3.0.2)
