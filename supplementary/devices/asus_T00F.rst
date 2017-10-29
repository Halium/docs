
Asus Zenfone 5 aka T00F/T00J
============================

Here only one or two sentences. What makes the device special? Is it a reference device? 

Status
------

Halium
^^^^^^

Halium 7.1 is being worked on by `Ilya Bizyaev <https://github.com/IlyaBizyaev>`_ and as of august 2017, he's got a **working x86 rootfs and LXC container** but test seem to fail. Here are `Device files <https://github.com/Halium/android_device_asus_T00F>`_ and `kernel <https://github.com/Halium/android_kernel_asus_T00F>`_. The local manifest has the following form

.. code-block:: guess

   <manifest>
     <remote name="zf" fetch="http://github.com/zenfone-legacy" revision="refs/heads/cm-14.1"/>
     <project name="Halium/android_device_asus_T00F" path="device/asus/T00F" remote="hal"/>
     <project name="Halium/android_kernel_asus_T00F" path="kernel/asus/T00F" remote="hal"/>
     <project name="proprietary_vendor_asus" path="vendor/asus" remote="zf"/>
     <project name="android_external_stlport" path="external/stlport" remote="los"/></manifest>

There is an  `issue in halium/projectmanagement <https://github.com/Halium/projectmanagement/issues/25>`_ for the T00F.

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
   * - No offical LineageOS `device page <https://wiki.lineageos.org/devices/hammerhead>`_
     - `android_device_placeholder <placeholder>`_
     - `android_kernel_placeholder <placeholder>`_ based on vX.Y.Z
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (version TODO)
~~~~~~~~~~~~~~~~~~~~~~~

TODO

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If other kernels exist, just make up headlines with a name that describe the origin (Cyanogemod, LineageOS, UBports, Canonical, ...) and which is the underlying mainline version. Afterwards describe what's been improved or altered and if possible why or what is still missing.

Device Specifics
----------------

Guides
^^^^^^

This should be populated with guides how to get into different boot modes and similar. For this device this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/blob/master/_data/devices/Z00T.yml>`_.

Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Usefull Ressources
^^^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
