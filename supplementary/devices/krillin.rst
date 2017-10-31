
krillin - BQ Aquaris E4.5
=========================

This device is besides having a smaller display almost identical to the Aquaris E5 so maybe images are interchangeable.

Status
------

Halium
^^^^^^

There is no one working on bringing Halium to this device AFAIK.

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
   * - Ubports 15.04 (Android 5.1 base) `device page <https://devices.ubports.com/#/krillin>`_
     - ?
     - ?
     - ?
     - ?
   * - Unofficial `LineageOS 13 device page <http://www.cyanogenmods.org/forums/topic/lineage-os-13-aquaris-e4-5-krillin-marshmallow-rom/>`_
     - `Pablito2020/android_device_bq_krillin <https://github.com/Pablito2020/android_device_bq_krillin>`_
     - `Pablito2020/android_kernel_bq_krillin <https://github.com/Pablito2020/android_kernel_bq_krillin>`_ based on 3.10.49
     - ?
     - some problems with SMS


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (4.13rc4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is no Mediatek MT-6582 device source tree present inside the mainline kernel yet.

Canonical's kernel (3.4.67 based)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The `kernel from canonical <https://github.com/bq/aquaris-E4.5/tree/aquaris-E4.5-ubuntu-master>`_ especially saw some backporting. AFAIK with this kernel every feature except radio worked.

Pablito2020 inofficial LOS kernel (3.10.49 based?)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This kernel (linked in table) seems to be more recent and is said to work completely with a CM13 base.

Device Specifics
----------------

Guides
^^^^^^

Entering Fastboot & Recovery Mode
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For `BQ Aquaris E4, E4.5, E5 and E6 <http://www.mibqyyo.com/en-articles/2016/01/20/recovery-menu-bq-phones/>`_\ , assuming *device is off*\ :

..

   Hold *Power* button + *Volume Up* button until menu pops up

   Boot Mode Selection:
   Navigate with *Volume Up*  and select with *Volume Down*

   Entering Recovery:
   Press *Volume Up* to access menu
   Navigate with *Volume* buttons and select with *Power* button.


Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Usefull Ressources
^^^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
