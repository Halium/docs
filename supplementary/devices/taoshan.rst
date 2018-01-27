
Taoshan - Sony Xperia L
=======================

The device is quite weak to run Halium. But it should be possible.

Status
------

Halium
^^^^^^
A port for Halium 7.1 is being worked on by `Jonatan Hatakeyama Zeidler <https://github.com/jonnius>`_. Halium 7.1 builds, but does not install using `halium-install <https://github.com/Halium/halium-scripts/>`_ due to TWRP BusyBox issues. Using `halium-install from JBB <https://github.com/JBBgameich/halium-install>`_ the halium reference rootfs can be installed, but it does not seem to start.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `LineageOS <https://wiki.lineageos.org/devices/taoshan>`_
     - `LineageOS/android_device_sony_taoshan <https://github.com/LineageOS/android_device_sony_taoshan>`_
     - `LineageOS/android_kernel_asus_msm8916 <https://github.com/LineageOS/android_kernel_asus_msm8916>`_ based on v3.4.0
     - Everything
     - Nothing
   * - `Halium Reference Rootfs <https://github.com/Halium/halium-devices/pull/33>`_
     - `jonnius/android_device_sony_taoshan <https://github.com/jonnius/android_device_sony_taoshan>`_
     - `jonnius/android_kernel_asus_msm8916 <https://github.com/jonnius/android_kernel_asus_msm8916>`_ based on v3.4.0
     - Installation
     - Does not boot
   * - `Plasma Mobile <https://github.com/Halium/halium-devices/pull/33>`_
     - `jonnius/android_device_sony_taoshan <https://github.com/jonnius/android_device_sony_taoshan>`_
     - `jonnius/android_kernel_asus_msm8916 <https://github.com/jonnius/android_kernel_asus_msm8916>`_ based on v3.4.0
     - Building images
     - Installation (/data is to small)
   * - UBPorts
     - None
     - None
     - Porting not yet started
     - Everything


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I don't know if something that is needed for the device is mainline already.

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kernel version is 3.4.0.

Device Specifics
----------------

Guides
^^^^^^

Special boot modes

- Fastboot: With the device powered off, while holding Volume Up, connect the USB cable to the computer. The LED should turn blue.

- Recovery: On boot, press Volume Down when the LEDs start lighting up. This only works with a working boot image. If there is none, you can flash twrp to boot partition first and use it to reboot into recovery.

- Second Recovery: To boot the FOTA Recovery, press Volume Up instead. This seems to be equal to Recovery.

Developer Info
^^^^^^^^^^^^^^

After flashing hybris-boot, recovery can not be accessed anymore. Therefore follow these steps to install halium rootfs:

- Enter Fastboot
- Flash `TWRP image <https://dl.TWRP.me/taoshan/>`_ to recovery and boot partition
- Reboot into TWRP on boot
- From TWRP reboot into Recovery
- In TWRP mount data partition
- Clone `halium-install from JBB <https://github.com/JBBgameich/halium-install>`_ (the official one does not work)
- Edit functions/core.sh and change rootfs size to 1G (data partition has only 1.6 GB)
- Run halium-install with halium rootfs image and system.img
- Enter Fastboot
- Flash hybris-boot image to boot partition using fastboot


Usefull Resources
^^^^^^^^^^^^^^^^^^
- `halium-install from JBB <https://github.com/JBBgameich/halium-install>`_
