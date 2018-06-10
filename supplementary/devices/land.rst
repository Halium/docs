
land - Redmi 3s/prime
===========================

Xiaomi Redmi 3s/prime is a entry-level phone with aggresive development on xda forums.
The prime variant is same but with a finger print and 3GB ram 

Status
------

Testing

Halium
^^^^^^

Device is booting into rootfs and LXC container starts without crashing
though i have to complete the other tests (Halium 7.1) ported by github.com/rupansh

Distributions
^^^^^^^^^^^^^

The following entries are just a placeholder, exactly as this sentence.

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `Unofficial LineageOS 14.1 Tree by hyper team <https://github.com/HyperTeam>`_
     - `HyperTeam/android_device_xiaomi_land <https://github.com/HyperTeam/android_device_xiaomi_land>`_
     - `HyperTeam/android_device_xiaomi_msm8937-common <https://github.com/HyperTeam/android_device_xiaomi_msm8937-common>`_
     - `HyperTeam/android_kernel_xiaomi_msm8937 <https://github.com/HyperTeam/android_kernel_xiaomi_msm8937>`_ based on v3.18.31
     - see device page
     - see device page
   * - `land on Halium projectmanagement <https://github.com/Halium/projectmanagement/issues/80>`_
     - `rupansh/android_device_xiaomi_land-1 <https://github.com/rupansh/android_device_xiaomi_land-1>`_
     - `rupansh/android_device_xiaomi_msm8937-common <https://github.com/HyperTeam/android_device_xiaomi_msm8937-common>`_
     - `rupansh/android_kernel_xiaomi_msm8937-1 <https://github.com/HyperTeam/android_device_xiaomi_msm8937-1>`_ based on v3.18.31
     - LXC container starts without crashing
     - yet to test everything else


Kernel & Hardware
^^^^^^^^^^^^^^^^^


CAF based
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The kernel is based off CAF's kernel. (Though it does have lineage specific patches) 

Device Specifics
----------------

Guides
^^^^^^

Unlocking the bootloader WILL void the warranty for this device

To unlock the bootloader, you need permission from MI

Press volume down + power button to enter fastboot mode

Press Volume Up + Volume Down + Power button to enter recovery mode

Developer Info
^^^^^^^^^^^^^^

Unlocking bootloader is cancerous for Xiaomi devices

Usefull Resources
^^^^^^^^^^^^^^^^^^

docs.halium.org for installation guide
