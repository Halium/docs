
a5xelte - Samsung Galaxy A5 2016
================================

Galaxy A5 2016 is an old device, though it is still quite popular.
It gets official LineageOS builds and is being maintained well.

Status
------

Halium
^^^^^^

There are two people on GitHub who have been working on this device.

manux176 (halium-9.0) progress: nothing but device manifest is made according to latest `issue state <https://github.com/Halium/projectmanagement/issues/260>`_

feuerpanda (halium-7.1) progress: device manifest if present, according to `issue state <https://github.com/Halium/projectmanagement/issues/155>`_, but it's closed so no progress is awaited.

Distributions
^^^^^^^^^^^^^

The following entries are just a placeholder, exactly as this sentence.

.. list-table::
   :header-rows: 1

   * - Distribution
     - XDA-Devs Forum Page
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - LineageOS `device page <https://wiki.lineageos.org/devices/a5xelte>`_
     - XDA-Devs `Forum page <https://forum.xda-developers.com/t/official-a5xelte-sm-a510f-lineage-os-17-1-for-a5-2016.4036151/>`_
     - `android_device_placeholder <https://github.com/LineageOS/android_device_samsung_a5xelte/tree/lineage-17.1>`_
     - `android_kernel_placeholder <https://github.com/LineageOS/android_kernel_samsung_universal7580/tree/lineage-17.1>`_ based on v3.10.108
     - Almost everything works, except entries in the section to the left.
     - IMS service (and won't work in future) since to Samsung's proprietary implementation.
   * - Ubports device page: no device page yet.
     - Ubports/Halium release on XDA-Devs forum: none as yet.
     - `android_device_placeholder <https://github.com/LineageOS/android_device_samsung_a5xelte/tree/lineage-17.1>`_
     - `android_kernel_placeholder <https://github.com/LineageOS/android_kernel_samsung_universal7580/tree/lineage-17.1>`_ based on v3.10.108
     - No porting done yet.
     - No porting done yet.


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (v3.10.108 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

LineageOS's `a5xelte device tree <https://github.com/LineageOS/android_device_samsung_a5xelte/tree/lineage-17.1>`_

TheMuppets' `a5xelte proprietary vendor tree <https://github.com/TheMuppets/proprietary_vendor_samsung/tree/lineage-17.1/a5xelte>`_

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



Device Specifics
----------------

Guides
^^^^^^

To get to Download mode: with the device powered off, hold ``Volume Down`` + ``Home`` + ``Power``.

To get to Recovery: with the device powered off, hold ``Volume Up`` + ``Home`` + ``Power``.

Developer Info
^^^^^^^^^^^^^^

I noticed very rare cases where the device would reboot after a few hours of use while on LineageOS 17.1 May update.

Useful Resources
^^^^^^^^^^^^^^^^
