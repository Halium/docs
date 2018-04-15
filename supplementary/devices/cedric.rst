
Cedric - Motorola Moto G5
=========================

The Moto G5 is a mid-range phone, with a few variants.

The XT1676 variant is special in that it has 3 GB of RAM.

.. todo::
    Document some other device variants.


Status
------

Maintainership
^^^^^^^^^^^^^^

.. list-table::
    :header-rows: 1
    
    * - Who
      - What
      - GitHub
      - XDA-Developer
      - Other Links
    * - Olivier
      - Initial documentation
      - reivilibre
      - LambdaPerl
      - n/a

Halium
^^^^^^

No progress to speak of, yet.

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - Unofficial LineageOS 14.1 (GitHub User: Wzedlare)
     - `android_device_motorola_cedric/cm-14.1 <https://github.com/Wzedlare/android_device_motorola_cedric/tree/cm-14.1>`_
     - `android_kernel_motorola_msm8937/cm-14.1 <https://github.com/Wzedlare/android_kernel_motorola_msm8937/tree/cm-14.1>`_ based on v3.18.49
     - The vast majority of things
     - ?
   * - Unofficial LineageOS 15.1 (GitHub User: Wzedlare)
     - `android_device_motorola_cedric/lineage-15.1 <https://github.com/Wzedlare/android_device_motorola_cedric/tree/lineage-15.1>`_
     - `android_kernel_motorola_msm8937/lineage-15.1 <https://github.com/Wzedlare/android_kernel_motorola_msm8937/tree/lineage-15.1>`_ based on v3.18.100
     - ?
     - ?

Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (v4.16-rc7 as of writing, 2018-03-31): Not Mainline
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is no device tree source (dts) file in the mainline kernel, neither for the device itself nor for the underlying SoC (MSM8937).
Consult the table below for status on other hardware.

.. list-table::
    :header-rows: 1
    
    * - Kind
      - Component
      - Progress
    * - Chipset/SoC
      - MSM8937 (msm8937.dts)
      - Not mainline yet. No known work yet.
    * - GPU
      - Adreno 505
      - YES, `mainline <https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/drivers/gpu/drm/msm/adreno/a5xx_gpu.c?h=v4.16-rc7>`_
    * - Image Sensor (Front)
      - OV5695 (5 MP)
      - **TODO**
    * - Image Sensor (Back)
      - IMX258 (13 MP)
      - **TODO**

Other hardware still needs research.

.. Write whether something that is needed for the device is mainline already (switch the version in the heading for what's recent when you write this). This means **device tree source files (.dts) as well as single drivers** (for example only the wifi driver).

Unofficial LineageOS 15.1 Android Kernel (3.18.100)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note: the 3.18.x branch of the Linux kernel has been marked as End-Of-Life (EOL).

Available at:

- Device Tree: https://github.com/Wzedlare/android_device_motorola_cedric/tree/lineage-15.1
- Kernel: https://github.com/Wzedlare/android_kernel_motorola_msm8937/tree/lineage-15.1
- Vendor Blobs: https://github.com/Wzedlare/android_vendor_motorola_cedric/tree/lineage-15.1

Unofficial LineageOS 14.1 Android Kernel (3.18.49)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I have included this, despite being less updated than the LOS15.1 version, as it (LOS 14.1) is what I use on my phone today.

Available at:

- Device Tree: https://github.com/Wzedlare/android_device_motorola_cedric/tree/cm-14.1
- Kernel: https://github.com/Wzedlare/android_kernel_motorola_msm8937/tree/cm-14.1
- Vendor Blobs: https://github.com/Wzedlare/android_vendor_motorola_cedric/tree/cm-14.1

Motorola Kernel Sources (?.??.???)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As used on the XT1676 devices. Not sure about the version, would have to check.

https://github.com/MotorolaMobilityLLC/kernel-msm/releases/tag/MMI-NPP25.137-15

Other devices have a different set of sources from Motorola.
Research may be required if someone is interested in locating them.


Device Specifics
----------------

Guides
^^^^^^

Unlocking the bootloader
~~~~~~~~~~~~~~~~~~~~~~~~

To unlock the bootloader, you have to provide a code to Motorola's online service who will warn you that your
warranty will be void before giving you an unlock code.

Be sure to back up your stock image if you want to return to it, as Motorola do not provide images
for this device, despite there being a friendly-looking 'stock ROMs' section on their developer site.

Once your device is unlocked, your boot photograph will be replaced by a warning with hard-coded text over the top of it.
You can change the boot photograph but the white text will always remain, so you need to use a boot photograph with white
in the correct region to prevent this from being visible.

.. Warning::
    There have been reports of hard-bricking devices by restoring stock, relocking the bootloader and
    updating through Motorola channels. Consult xda-developer threads about this issue if this concerns you.
    (If you don't intend on returning to stock, this is likely not a concern.)
    
.. todo::
    TODO provide a nice link to help users unlock their bootloader


Access the bootloader 
~~~~~~~~~~~~~~~~~~~~~

When your device is turned off:
Hold down the Volume-Down button whilst you hold down the Power button.
Within a few seconds, you should be greeted by the bootloader menu.

Use Volume-Up and Volume-Down to choose between the choices (such as 'Start',
'Recovery', 'Restart Bootloader', amongst others) and press Power to activate your choice.

.. This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_.

Developer Info
^^^^^^^^^^^^^^

.. Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

The XT1676 had `segmentation faults <https://forum.xda-developers.com/g5/how-to/segmentation-fault-customs-roms-t3682734>`_ with a particular (kernel?) configuration under LineageOS 14.1 and other custom Android versions. Investigation may be required to track down the cause and solution in the event that the Halium porting effort runs into it again.


Useful Resources
^^^^^^^^^^^^^^^^

.. todo::
    Provide some useful resources here.

.. If anything might be usefull but didn't fit above you can just throw in some links here.
