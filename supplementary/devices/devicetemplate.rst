
Codename - Template Device
===========================

**//Disclaimer:** Please remove everything that is just part of this template and not actually about the device before submitting this into the official wiki, thank you! **//**

Here only one or two sentences. What makes the device special? Is it a reference device? 

Status
------

Halium
^^^^^^

Of course we are mainly interested in Halium status. Therefore please state 


* Is someone already working on Halium for this device? If YES: link to repositories of **device specific files** (usually github repos called "android_device_manufacturer_codename") and **device kernel** (usually a repo beginning with "android\ *kernel*\ ") and name authors if possible (perhaps link to their github profile)
* Is Halium working for this device? If YES: Name the android base version (5.1 or 7.1) and everything you know about the actual status (what's working, which rootfs, ...)

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
   * - LineageOS placeholder `device page placeholder <placeholder>`_
     - `android_device_placeholder <placeholder>`_
     - `android_kernel_placeholder <placeholder>`_ based on vX.Y.Z
     - ?
     - ?
   * - Ubports placeholder `device page placeholder <placeholder>`_
     - `android_device_placeholder <placeholder>`_
     - `android_kernel_placeholder <placeholder>`_ based on vX.Y.Z
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (vX.Y.Z as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Write whether something that is needed for the device is mainline already (switch the version in the heading for what's recent when you write this). This means **device tree source files (.dts) as well as single drivers** (for example only the wifi driver).

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If other kernels exist, just make up headlines with a name that describe the origin (Cyanogemod, LineageOS, UBports, Canonical, ...) and which is the underlying mainline version. Afterwards describe what's been improved or altered and if possible why or what is still missing.

Device Specifics
----------------

Guides
^^^^^^

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_.

Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Usefull Ressources
^^^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
