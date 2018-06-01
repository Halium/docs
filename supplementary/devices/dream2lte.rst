
dream2lte - Samsung Galaxy S8+
==============================

The Samsung Galaxy S8+ (shortened to S8+) are Android smartphones produced by Samsung Electronics as part of the Samsung Galaxy S series. The S8+ was unveiled on 29 March 2017 and directly succeeds the Samsung Galaxy S7 Edge.

Status
------

Halium
^^^^^^

Halium 7.1 is **WIP**. Ported by  `Ivan Semkin <https://github.com/vanyasem>`_.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Device Common Files
     - Kernel
     - What works
     - What doesn't work
   * - `dream2lte on XDA <https://forum.xda-developers.com/galaxy-s8+/development/rom-unofficial-lineageos-14-1-galaxy-s8-t3684398>`_
     - `universal8895/android_device_samsung_dream2lte <https://github.com/universal8895/android_device_samsung_dream2lte>`_
     - `universal8895/android_device_samsung_universal8895-common <https://github.com/universal8895/android_device_samsung_universal8895-common>`_
     - `universal8895/android_kernel_samsung_universal8895 <https://github.com/universal8895/android_kernel_samsung_universal8895>`_ based on v4.4.79
     - see device page
     - see device page
   * - `dream2lte on Halium projectmanagement <https://github.com/Halium/projectmanagement/issues/64>`_
     - `universal8895/android_device_samsung_dream2lte <https://github.com/universal8895/android_device_samsung_dream2lte>`_
     - `vanyasem/android_device_samsung_universal8895-common <https://github.com/vanyasem/android_device_samsung_universal8895-common>`_
     - `vanyasem/android_kernel_samsung_universal8895 <https://github.com/vanyasem/android_kernel_samsung_universal8895>`_ based on v4.4.79
     - see device page
     - see device page


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Both **Halium and LOS share a common base** which is Cyanogenmod. However, the Halium kernel was patched with Halium-specific edits.

Device Specifics
----------------

Guides
^^^^^^

Unlocking the bootloader will permanently set your device's KNOX to 0x1, which will disable Knox-related functionality even if you re-lock your device later.

The device doesn't have fastboot, you need to flash it using `Heimdall <https://github.com/Benjamin-Dobell/Heimdall>`_.

To unlock the bootloader enable ``OEM Unlock`` setting in Developer Options of your ROM.

In order to launch download mode, with the device powered off, hold ``Volume Down`` + ``Bixby`` + ``Power``.

In order to launch recovery, with the device powered off, hold ``Volume Up`` + ``Bixby`` + ``Power``.

Useful Resources
^^^^^^^^^^^^^^^^

* `Repo Manifest <https://github.com/Halium/halium-devices/blob/halium-7.1/manifests/samsung_dream2lte.xml>`_
* `TWRP for Samsung Galaxy S8+ <https://twrp.me/samsung/samsunggalaxys8plus.html>`_
