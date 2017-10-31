
Bullhead - Nexus 5X
===================

This is supposed to become one of our **reference devices**.

Status
------

Halium
^^^^^^

Halium is being worked on for this device. You can find the sources in the table below.

.. todo::
    Add the manifest for Bullhead

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `Bullhead on LineageOS Wiki <https://wiki.lineageos.org/devices/bullhead>`_
     - `LineageOS/android_device_lge_bullhead <https://github.com/LineageOS/android_device_lge_bullhead>`_
     - `LineageOS/android_kernel_lge_bullhead <https://github.com/LineageOS/android_kernel__lge_bullhead>`_ based on v3.10.73
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline Kernel (4.13rc4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is **no device tree source** (dts) file in the mainline kernel, neither for the device itself nor for the underlying SoC (MSM8992). The general support for Nexus 5X and Nexus 6 landed with 4.10, according to a `Phoronix article about Kernel 4.10 ARM support <http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.10-ARM-Tegra-More>`_. There is also `a short slideshow by Jeremy McNicoll about the initial and ongoing mainlining process <http://events.linuxfoundation.org/sites/events/files/slides/JRM_NEXUS_ELC_2017.pdf>`_.

LOS 14.1 Android Kernel (3.10.73)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unclear whether security bug fixes are implemented into this kernel (long term 3.10 kernel @ kernel.org has version 3.10.107). 

Device Specifics
----------------

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_. For now check the LOS device page linked in the table above.
