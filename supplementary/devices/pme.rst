
PME (Perfume) - HTC 10
======================

In 2015, HTC released the HTC One M9 smartphone, which was praised for its design, but criticized for being too similar to its predecessor, the HTC One (M8). To address the shortcomings of the M9, HTC released another new phone that year with a new design and hardware: the HTC One A9. The design of the HTC 10 is somewhat of a mix of the M9 and the A9

Status
------

Halium
^^^^^^

A port for Halium 7.1 is being worked on by `Ivan Semkin <https://github.com/vanyasem>`_ and `Marius Gripsgard <https://github.com/mariogrip>`_

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `PME on LineageOS Wiki <https://wiki.lineageos.org/devices/pme>`_
     - `LineageOS\android_device_htc_pme <https://github.com/LineageOS/android_device_htc_pme>`_
     - `LineageOS\android_kernel_htc_msm8996 <https://github.com/LineageOS/android_kernel_htc_msm8996>`_ based on v3.18.31
     - see device page
     - see device page
   * - `PME on Halium projectmanagement <https://github.com/Halium/projectmanagement/issues/28>`_
     - `Halium/android_device_htc_pme <https://github.com/Halium/android_device_htc_pme>`_
     - `Halium/android_kernel_htc_msm8996 <https://github.com/Halium/android_kernel_htc_msm8996>`_ based on v3.18.31
     - see device page
     - see device page


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (vX.Y.Z as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Write whether something that is needed for the device is mainline already (switch the version in the heading for what's recent when you write this). This means **device tree source files (.dts) as well as single drivers** (for example only the wifi driver).

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Both **Halium and LOS share a common base** which is Cyanogenmod. However, the Halium kernel was pacthed with Halium-specific edits. Currently only kernel flags in ``pme_defconfig`` were altered.

Device Specifics
----------------

Guides
^^^^^^

HTC allowed users to officially unlock phones without S-Off. Links provided below

This device has 2 modes for fastboot: ``bootloader`` (white backgrond) and ``download`` (dark background). You have to use ``download`` mode in order to flash/wipe anything. AFAIK bootloader mode is only used to check its status and for emergency purposes.

In order to launch recovery, you have to boot into ``download`` mode first (Power + Volume Down), then select ``reboot to bootloader``, and only then ``boot to recovery mode``.

Also, be sure to check `the LineageOS device info for PME <https://github.com/LineageOS/lineage_wiki/blob/master/_data/devices/pme.yml>`_

Developer Info
^^^^^^^^^^^^^^

This device is mostly open and has no weird behaviour

Useful Resources
^^^^^^^^^^^^^^^^

* `Repo Manifest <https://gist.github.com/vanyasem/64fa7fdc0df556561c50a6048a982ce1>`_
* `Official HTC Unlock guide <https://www.htcdev.com/bootloader/>`_
* `TWRP for HTC 10 <https://eu.dl.twrp.me/pme/>`_
