
rolex - Xiaomi Redmi 4a
===========================

A Snapdragon 425 (MSM8917) budget phone from Xiaomi released in 2016 that is great on its own. Comes with MIUI 8 (Marshmallow), upgradeable to MIUI 9 (Nougat).

Its has 2GB LPDDR3 RAM, 16GB/32GB eMMC storage.

An updated version of this device Redmi 5a (riva) was released in 2017. Both are basically same, have same device tree and kernels. So anything that applies to 4a should as it is apply to 5a

Status
------

Halium
^^^^^^

Halium 7.1 is **WIP**. Ported by `echosalik <https://github.com/echosalik>`_

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
   * - `Unofficial LineageOS 14.1 Tree by LineageOS-R4A <https://github.com/LineageOS-R4A/>`_
     - `LineageOS-R4A/android_device_xiaomi_rolex <https://github.com/LineageOS-R4A/android_device_xiaomi_rolex>`_
     - NA
     - `LineageOS-R4A/android_kernel_xiaomi_msm8917 <https://github.com/LineageOS-R4A/android_kernel_xiaomi_msm8917>`_ based on v3.18.31
     - see device page
     - see device page
   * - `rolex on Halium projectmanagement <https://github.com/Halium/projectmanagement/issues/92>`_
     - `echosalik/android_device_xiaomi_rolex <https://github.com/echosalik/android_device_xiaomi_rolex>`_
     - NA
     - `echosalik/android_kernel_xiaomi_msm8917 <https://github.com/echosalik/android_kernel_xiaomi_msm8917>`_ based on v3.18.31
     - see projectmanagement issue
     - see projectmanagement issue


Kernel & Hardware
^^^^^^^^^^^^^^^^^

The kernel is based off LineageOS-R4A's kernel (though it has some halium specific patches).

**camera** folder from device tree had to be removed due to an missing dependency that I couldn't resolve.

Device Specifics
----------------

Guides
^^^^^^

Unlocking the bootloader WILL void the warranty for this device.

To unlock the bootloader, you need to get the permission from Xiaomi. Takes around a week or two. It is rather simple.

Press Volume Down + Power Button to enter fastboot mode.

Press Volume Up + Volume Down + Power button to enter recovery mode.

Useful Resources
^^^^^^^^^^^^^^^^^^

`TWRP XDA Link <https://forum.xda-developers.com/redmi-4a/development/recovery-twrp-3-1-0-0-xiaomi-redmi-4a-t3576024>`_