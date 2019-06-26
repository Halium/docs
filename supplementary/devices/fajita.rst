
Fajita - Oneplus 6(T)
===========================

The OnePlus 6T is an Android-based smartphone from OnePlus. It was announced on October 29, 2018, before being released on November 6.
The OnePlus 6T is an incremental hardware update to the OnePlus 6, removing the 3.5 mm audio jack, making the notch at the top of the screen into a smaller "teardrop" size, and providing an in-display fingerprint sensor.

Status
------

Halium
^^^^^^
No progress to speak of, yet.

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
   * - `Oneplus6T on XDA <https://forum.xda-developers.com/oneplus-6t/development/rom-lineageos-16-0-t3897334>`_
     - `LineageOS/android_device_oneplus_fajita <https://github.com/LineageOS/android_device_oneplus_fajita>`_
     - Stock Kernel?
     - Everything
     - Does not have kernel source to look into
   * - `Oneplus6T on XDA <https://forum.xda-developers.com/oneplus-6t/development/rom-omnirom-oneplus6t-t3888582>`_
     - `omnirom/android_device_oneplus_oneplus6t <https://github.com/omnirom/android_device_oneplus_oneplus6t>`_
     - `omnirom/android_kernel_oneplus_sdm845 <https://github.com/omnirom/android_kernel_oneplus_sdm845>`_ based on v4.9.112
     - Everything
     - None as of now



Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (v4.9.112 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Almost all of the drivers is already mainlined in omnirom.
LineageOS kernel is not available in git at the time of documenting, they seems to be using stock kernel.

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Not available as at the time of writing

Omnirom kernel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Omnirom Kernel is one big mess of 673,832 commits merged from different repositories.
Every drivers work including fingerprint sensor.

Device Specifics
----------------

Guides
^^^^^^

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_.

Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Useful Resources
^^^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
