
Nexus 5X aka Bullhead
=====================

This is supposed to become one of our **reference devices**.

Status
------

Halium
^^^^^^

Halium is **being worked on for this device**. You can find the `kernel here <https://github.com/Halium/android_kernel_lge_bullhead>`_ and the `device files here <https://github.com/Halium/android_device_lge_bullhead>`_.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - LineageOS 14.1 `info page <https://wiki.lineageos.org/devices/bullhead>`_
     - `android_device_lge_bullhead <https://github.com/LineageOS/android_device_lge_bullhead>`_
     - `android_kernel_lge_bullhead <https://github.com/LineageOS/android_kernel__lge_bullhead>`_ based on v3.10.73
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline Kernel (4.13rc4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is **no device tree source** (dts) file in the mainline kernel, neither for the device itself nor for the underlying SoC (MSM8992). The general support for Nexus 5X and Nexus 6 landed with 4.10 according to `phoronix <http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.10-ARM-Tegra-More>`_. A short slideshow by Jeremy McNicoll about the initial and ongoing mainlining process already happening is `hosted by the linux foundation here <http://events.linuxfoundation.org/sites/events/files/slides/JRM_NEXUS_ELC_2017.pdf>`_.

LOS 14.1 Android Kernel (3.10.73)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unclear whether security bug fixes are implemented into this kernel (long term 3.10 kernel @ kernel.org has version 3.10.107). 

Device Specifics
----------------

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_. For now check the LOS device page linked in the table above.
