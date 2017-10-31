
Flo - Nexus 7 (2013 Wifi only)
==============================

This is not being worked on right now, however it's the most mainline phone besides the N900 AFAIK.

Status
------

Halium
^^^^^^

There are currently no effort to get Hallium to work on Flo directly although there is work being done to port it to the `Nexus 7 (2013 LTE) aka deb by user doniks <https://forums.ubports.com/topic/431/porting-halium-to-nexus-7-deb>`_. There seem to be cases were images work on both phones which should be the case since deb is flo with additional mobile network capabilites.

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

John Stultz from Linaro has been working some time on getting everything for the Nexus 7 mainline and the most promising candidate to try on this device should be `one of his kernel branches <https://git.linaro.org/people/john.stultz/flo.git/>`_. The 4.10 branch is just 23 commits different from mainline!

LOS 14.1 Android Kernel (3.4.0)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unclear whether security bug fixes are implemented into this kernel (long term 3.4 kernel @ kernel.org has version 3.4.113). 

Canonical's Ubuntu Touch Kernel (3.4.0 based)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This is listed because it used the kernel backports to integrate newer drivers in the orginal vendor kernel which might be usefull in some cases. It can be found `here <https://launchpad.net/ubuntu/+source/linux-flo>`_.

Device Specifics
----------------

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_. For now check the LOS device page linked in the table above.
