
mako - Nexus 4
==============

As all Nexii rather good support of sources.

Status
------

Halium
^^^^^^

Work in progress.

Sources:

* `Kernel <https://github.com/110101011/lge-kernel-mako>`_
* `Device <https://github.com/110101011/android_device_lge_mako>`_
* `Vendor <https://github.com/110101011/proprietary_vendor_lge>`_

What works:

* Halium boots with reference rootfs
* LED
* Vibrator
* Wifi
* Buttons
* Graphics
* Battery

What doesn't work (or isn't tested yet):

* Audio
* Camera

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `Mako on LineageOS Wiki <https://wiki.lineageos.org/devices/mako>`_
     - `LineageOS/android_device_lge_mako <https://github.com/LineageOS/android_device_lge_mako>`_
     - `LineageOS/android_kernel_lge_mako <https://github.com/LineageOS/lge-kernel-mako>`_ based on v3.4.0
     - ?
     - ?
   * - Ubports 15.04 (Android 5.1 base) `device page <https://devices.ubports.com/#/mako>`_
     - ?
     - ?
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (4.13rc4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No exact device tree source (dts) for mako so far. But a general dts for the underlying SoC (APQ8064) is available and also used for other specific dts'ses (e.g.) Nexus 7) 

LineageOS kernel (3.4.0 based)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

TODO

Canonical's Ubuntu Touch kernel (3.4.0 based)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Available `here <https://launchpad.net/ubuntu/+source/linux-mako>`_.

Device Specifics
----------------

Guides
^^^^^^

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_.

Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Usefull Ressources
^^^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
