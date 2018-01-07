
Deb - Nexus 7 (2013 GSM)
========================

This should probably **also work for the Wifi edition (flo)**.

Status
------

Halium
^^^^^^

**Halium 7.1 is working for this device** thanks to `doniks <https://github.com/doniks>`_. There is a detailed log by doniks in  `the ubports forums <https://forums.ubports.com/topic/431/porting-halium-to-nexus-7-deb>`_ and a `halium/projectmanagement issue <https://github.com/Halium/projectmanagement/issues/22>`_. The sources are linked in the forum post.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - LineageOS 14.1 `info page <https://wiki.lineageos.org/devices/flo>`_
     - `android_device_asus_flo <https://github.com/LineageOS/android_device_asus_flo>`_
     - `android_kernel_google_msm <https://github.com/LineageOS/android_kernel_google_msm>`_ based on v3.4.0
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline Kernel (4.13rc4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Most of the drivers is already mainlined. Check John Stultzes kernel below for what is missing.

The "John Stultz" almost mainline Kernel (4.11 latest)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

John Stultz from Linaro has been working some time on getting everything for the Nexus 7 mainline and the most promising candidate to try on this device should be `one of his kernel branches <https://git.linaro.org/people/john.stultz/flo.git/>`_. The 4.10 branch is just 23 commits different from mainline! See here a `post from John on the mainlining effort <https://plus.google.com/111524780435806926688/posts/S4ajVewveSR>`_.

LOS 14.1 Android Kernel (3.4.0)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unclear whether security bug fixes are implemented into this kernel (long term 3.4 kernel @ kernel.org has version 3.4.113). 

Canonical's Ubuntu Touch Kernel (3.4.0 based)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This is listed because it used the kernel backports to integrate newer drivers in the orginal vendor kernel which might be usefull in some cases. It can be found `here <https://launchpad.net/ubuntu/+source/linux-flo>`_.

Device Specifics
----------------

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_. For now check the LOS device page linked in the table above.
