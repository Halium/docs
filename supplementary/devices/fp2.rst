
FP2 - Fairphone 2
==================

The Fairphone 2 is the smartphone made with highest priority for fair production worldwide (AFAIK) and extremely easy to repair (compared to other phones), This makes this a great candidate for a reference device ;-)

Status
------

Halium
^^^^^^

There are reports of Halium running on the device `here <http://blog.bshah.in/slides/akademy2017/#4>`_\ , however the locations of the sources are unknown to the author at the moment.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - Ubports 15.04 (Android 5.1 base) `device page <https://devices.ubports.com/#/FP2>`_
     - `android_device_fairphone_fp2 <https://github.com/ubports/android_device_fairphone_fp2>`_
     - `android_kernel_fairphone_fp2 <https://github.com/ubports/android_kernel_fairphone_fp2>`_ based on v3.4.0
     - ?
     - ?


Also there is an `official page by the manufacturer <https://support.fairphone.com/hc/en-us/articles/204642759-What-operating-system-OS-does-the-Fairphone-2-run-on->`_ dedicated to list more.

Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (4.13rc4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is no device tree source inside the mainline kernel specific to the FP2. However, the underlying SoC is present `(MSM8974) <https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm/boot/dts/qcom-msm8974.dtsi?h=v4.13-rc4>`_. 

UBports kernel (3.4.0 base)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

This is probably taken from the Fairphone sources directly and patched with the Ubuntu Touch specific stuff, need to check this further to be sure...

Device Specifics
----------------

Guides
^^^^^^

This should be populated with guides how to get into different boot modes and similar. 

Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Usefull Ressources
^^^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
