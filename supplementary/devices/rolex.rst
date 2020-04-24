
rolex - Xiaomi Redmi 4a
===========================

A Snapdragon 425 (MSM8917) budget phone from Xiaomi released in 2016 that is great on its own. Comes with MIUI 8 (Marshmallow), upgradeable to MIUI 9 (Nougat).

It has 2GB LPDDR3 RAM, 16GB/32GB eMMC storage.

An updated version of this device Redmi 5a (riva) was released in 2017. Both are basically the same, and share device trees and kernels. So anything that applies to 4a should as well apply to 5a

Status
------

Halium
^^^^^^

Halium 7.1 is **WIP**. Ported by `areyoudeveloper(Tea) <https://github.com/areyoudeveloper>`_

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
   * - `Unofficial LineageOS 14.1 Tree by murali <https://github.com/muralivijay/>`_
     - `muralivijay/android_device_xiaomi_rolex <https://github.com/muralivijay/android_device_xiaomi_rolex>`_
     - NA
     - `Nick89786/android_kernel_xiaomi_msm8917 <https://github.com/Nick89786/android_kernel_xiaomi_msm8917>`_ based on v3.18.140
     - see device page
     - see device page
   * - `rolex on Halium projectmanagement <https://github.com/ubports/porting-notes/wiki/Xiaomi-Redmi-4(A)-(xiaomi-rolex)>`_
     - `areyoudeveloper1/android_device_xiaomi_rolex <https://github.com/areyoudeveloper1/android_device_xiaomi_rolex>`_
     - NA
     - `areyoudeveloper1/android_kernel_xiaomi_msm8917 <https://github.com/areyoudeveloper1/android_kernel_xiaomi_msm8917>`_ based on v3.18.140
     - see projectmanagement issue
     - see projectmanagement issue


Kernel & Hardware
^^^^^^^^^^^^^^^^^

The kernel is based off nick's kernel (though it has some halium specific patches).

Device Specifics
----------------

Guides
^^^^^^

Unlocking the bootloader WILL void the warranty for this device.

To unlock the bootloader, you need to get the permission from Xiaomi. Takes around a week or two. `Offical Guide <http://en.miui.com/thread-246705-1-1.html>`_.

Press Volume Down + Power Button to enter fastboot mode.

Press Volume Up + Power button to enter recovery mode.

Useful Resources
^^^^^^^^^^^^^^^^^^

`TWRP XDA Link <https://forum.xda-developers.com/redmi-4a/development/recovery-twrp-3-1-0-0-xiaomi-redmi-4a-t3576024>`_
