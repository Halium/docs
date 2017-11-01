
Wifi
====

Tests
-----

Testing wifi is done using NetworkManager

.. code-block:: guess

   nmcli d

Qcom devices
------------

Wifi is fairly easy to get going on most Qcom based devices

.. code-block:: guess

   echo 1 > /dev/wcnss_wlan
   echo sta > /sys/module/wlan/parameters/fwpath

That should enable wifi

broadcom bcmdhd
---------------

It is recommended to modularize bcmdhd drivers since that will ensure use of HW MAC address.

In the kernel defconfigs, make sure these settings are set

.. code-block:: guess

   CONFIG_MODULES=y
   CONFIG_BCMDHD=m

Then add this to your devices init.rc file, it's recomended to set this in early stages to avoid race condition with network manager (\ ``on post-fs-data`` is a good place for this)

.. code-block:: guess

   insmod /system/lib/modules/bcmdhd.ko
