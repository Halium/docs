
Taoshan - Sony Xperia L
===========================

The device is quite weak to run Halium. But it should be possible.

Status
------

Halium
^^^^^^
A port for Halium 7.1 is being worked on by `Jonatan Hatakeyama Zeidler <https://github.com/jonnius>`_ (`Device Tree <https://github.com/jonnius/android_device_sony_taoshan>` and `Kernel <https://github.com/jonnius/android_kernel_sony_msm8930/tree/halium>`). Halium 7.1 builds, but does not install using halium-install. Using halium-install from JBB it fails to copy the rootfs.img to /data.

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

Mainline (v3.4.0 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I don't know if something that is needed for the device is mainline already.

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Both **Halium and LOS share a common base** which is Cyanogenmod. However, the Halium kernel was pacthed with Halium-specific edits. Currently some kernel flags and additional patches were used.

Device Specifics
----------------

Guides
^^^^^^

Special boot modes

    Fastboot: With the device powered off, while holding Volume Up, connect the USB cable to the computer. The LED should turn blue.

    Recovery: On boot, press Volume Down when the LEDs start lighting up.

    Second Recovery: To boot the FOTA Recovery, press Volume Up instead.

Developer Info
^^^^^^^^^^^^^^

I do not know of any strange behaviour of some kind.

Usefull Ressources
^^^^^^^^^^^^^^^^^^

I do not know of any usefull ressources, yet.
