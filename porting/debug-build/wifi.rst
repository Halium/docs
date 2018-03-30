
Wifi
====

Enabling Wi-Fi hardware
-----------------------

Qualcomm
^^^^^^^^

Wifi is fairly easy to get going on most Qualcomm devices. The following should enable your device's Wi-Fi hardware::

   echo 1 > /dev/wcnss_wlan
   echo sta > /sys/module/wlan/parameters/fwpath

Broadcom bcmdhd
^^^^^^^^^^^^^^^

It is recommended to build Broadcom drivers as a module since that will ensure use of the device's MAC address.

In the kernel defconfigs, make sure these settings are set::

   CONFIG_MODULES=y
   CONFIG_BCMDHD=m

Then add this to your device's init.rc file, it's recommended to set this in early stages to avoid race condition with network manager (\ ``on post-fs-data`` is a good place for this)::

   insmod /system/lib/modules/bcmdhd.ko

Testing Wi-Fi functionality
---------------------------

You may run the following command to see if your Wi-Fi hardware has come up::

    nmcli d

Your device should show up as ``wlan0`` and have a state of "Disconnected" when it is ready. At that point, run the following command to enter an interface that you can use to connect to Wi-Fi::

    nmtui

Once you are connected to Wi-Fi, try pinging an Internet device::

    ping 8.8.8.8

If all of this is successful, you have successfully brought up your Wi-Fi hardware. If not, check your device's :ref:`logcat` for possible errors.

Common errors
-------------

Kernel 3.10 ping: ``socket: Permission denied``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This error is most common on devices which shipped with Linux kernel 3.10. To resolve it, apply the following patches:

#. `Introduce the SECURITY_ANDROID_GID_CAPABILITIES option`_
#. `Select SECURITY_ANDROID_GID_CAPABILITIES when enabling paranoid network`_
#. `Enable the CONFIG_SECURITY_ANDROID_GID_CAPABILITIES option`_


.. _Introduce the SECURITY_ANDROID_GID_CAPABILITIES option: https://github.com/Halium/android_kernel_lge_bullhead/commit/3f8345978921875227cd20c09d6deff05778c923
.. _Select SECURITY_ANDROID_GID_CAPABILITIES when enabling paranoid network: https://github.com/Halium/android_kernel_lge_bullhead/commit/91506c596892de2160799cf69282a7488fdd24ca
.. _Enable the CONFIG_SECURITY_ANDROID_GID_CAPABILITIES option: https://github.com/Halium/android_kernel_lge_bullhead/commit/0b64b0cd08b1b79eb4a26aa40651d7ff0a4fff3c