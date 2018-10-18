
Nicki - Sony Xperia M
===========================

Xperia M is very weak, especially by today's standards. But it runs Halium. Somehow.

Status
------

Halium
^^^^^^

There is an ongoing port of Halium for Nicki that `Konrad Dybcio <https://github.com/ewentual>`_ is working on. Halium-7.1 branch builds with slightly tweaked LOS 14 sources (manifest will be published soon). Halium rootfs can be flashed using `halium-install by JBB <https://github.com/JBBgameich/halium-install>`_, yet /data partition is too small (2 gigs) to fit a plasma mobile rootfs. This can be worked around by changing `IMAGE_SIZE=2G` to for example `IMAGE_SIZE=1.7G` for `pm` in halium-install/functions/distributions.sh.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `LineageOS <https://wiki.lineageos.org/devices/nicki>`_
     - `android_device_sony_nicki <https://github.com/lineageos/android_device_sony_nicki>`_
     - `android_kernel_sony_msm8x27 <https://github.com/lineageos/android_kernel_sony_msm8x27>`_ based on v3.4.0
     - Everything(afaik)
     - Nothing
   * - Halium Reference Rootfs
     - `ewentual/halium_device_sony_nicki <https://github.com/ewentual/halium_device_sony_nicki>`_
     - `ewentual/halium_kernel_sony_msm8x27 <https://github.com/ewentual/halium_kernel_sony_msm8x27>`_ based on v3.4.0
     -  See projectmanagement issue
     - Everything else
   * - Ubports
     - Not yet
     - Not yet
     - Nothing, even putting rootfs on the device (not enough space)
     - Everything


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Not present

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kernel version is v3.4.0.

Device Specifics
----------------

Guides
^^^^^^

Special boot modes

Fastboot: With the device powered off, while holding Volume Up, connect the USB cable to the computer. The LED should turn blue.

Flashmode: With the device powered off, while holding Volume Down, connect the USB cable to the computer. The LED should turn green. Then you can go back to the stock rom using _`Androxyde's Flashtool <http://www.flashtool.net/downloads.php>`_ Last sure to be working version of flashtool working with nicki was 0.9.18.6, newer versions could fail.

Recovery (ONLY on android custom kernels): On boot, press Volume Down when the LEDs start lighting up. This only works with a working boot image. If there is none, you can flash twrp to boot partition first and use it to reboot into recovery.

Second Recovery: To boot the FOTA Recovery, press Volume Up instead. This seems to be equal to Recovery.

Developer Info
^^^^^^^^^^^^^^

With hybris-boot only way to access TWRP is to flash it as boot.

Useful Resources
^^^^^^^^^^^^^^^^^^

- `halium-install from JBB <https://github.com/JBBgameich/halium-install>`_
