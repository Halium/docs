
Taoshan - Sony Xperia L
===========================

The device is quite weak to run Halium. But it should be possible.

Status
------

Halium
^^^^^^
A port for Halium 7.1 is being worked on by `Jonatan Hatakeyama Zeidler <https://github.com/jonnius>`_ (`Device Tree <https://github.com/jonnius/android_device_sony_taoshan>` and `Kernel <https://github.com/jonnius/android_kernel_sony_msm8930/tree/halium>`). Halium 7.1 builds, but does not install using halium-install due to twrp busybox issues. Using halium-install from JBB the halium reference rootfs can be installed, but it does not seem to start.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `taoshan on LineageOS Wiki <https://wiki.lineageos.org/devices/taoshan>`_
     - `LineageOS/android_device_sony_taoshan <https://github.com/LineageOS/android_device_sony_taoshan>`_
     - `LineageOS/android_kernel_asus_msm8916 <https://github.com/LineageOS/android_kernel_asus_msm8916>`_ based on v3.4.0
     - see device page
     - see device page


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

    Fastboot: With the device powered off, while holding Volume Up, connect the USB cable to the computer. The LED should turn blue.

    Recovery: On boot, press Volume Down when the LEDs start lighting up. This only works with a working boot image. If there is none, the LineageOS boot image can be flashed to boot partition first.

    Second Recovery: To boot the FOTA Recovery, press Volume Up instead. This seems to be equal to Recovery.

Developer Info
^^^^^^^^^^^^^^

After flashing hybris-boot, recovery can not be accessed anymore. Therefore extract LineageOS boot image from `LineageOS build for taoshan <https://download.lineageos.org/taoshan>_` to boot partition (using fastboot) and `twrp image <https://dl.twrp.me/taoshan/>_` to recovery. Enter recovery and use twrp to mount /data. The size of the data partition is only 1.6 GB, which is enough for the halium reference rootfs. Clone `halium-install from JBB <https://github.com/JBBgameich/halium-install>` (the official one does not work). Edit functions/core.sh and change rootfs size to 1G. Then run halium-install with halium reference rootfs and the halium system.img.

Usefull Ressources
^^^^^^^^^^^^^^^^^^
`halium-install from JBB <https://github.com/JBBgameich/halium-install>`    
    
