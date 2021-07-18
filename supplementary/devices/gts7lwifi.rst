
gts7lwifi - Samsung Galaxy Tab S7 (Wi-Fi)
=========================================

Samsung's Galaxy Tab S7 is the most successfull Android tablet for now. It features great specifications alongside with great price value, but OneUI is still not the replacement of any PC OS (neither iPadOS is).
Porting Ubuntu Touch seems a good idea for those, how want to combine entertainment and productivity!

Status
------

**Development freezed until the complete device tree is released.**

Halium
^^^^^^

Nobody has succeed in porting Halium on the device yet, neither I pretend to do, but I will do my best to do so. Because I want to see fully functional OS on my new favourite tablet.

Halium status is: nothing's been done yet, I'm trying to get along with documentation and quick guides to start my journey.

Current maintainer: `scriptSQD <https://github.com/scriptSQD>`_.

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
   * - LineageOS builds: none yet
     - `Bush-cat/android_device_samsung_gts7-common <https://github.com/Bush-cat/android_device_samsung_gts7-common>`_
     - `miraclestars/android_device_samsung_sm8250-common <https://github.com/miraclestars/android_device_samsung_sm8250-common>`_
     - `scriptSQD/android_kernel_samsung_gts7lwifi <https://github.com/scriptSQD/android_kernel_samsung_gts7lwifi>`_ based on v4.19.113
     - ?
     - ?
   * - UBPorts device page: none yet
     - `Bush-cat/android_device_samsung_gts7-common <https://github.com/Bush-cat/android_device_samsung_gts7-common>`_
     - `miraclestars/android_device_samsung_sm8250-common <https://github.com/miraclestars/android_device_samsung_sm8250-common>`_
     - `scriptSQD/android_kernel_samsung_gts7lwifi <https://github.com/scriptSQD/android_kernel_samsung_gts7lwifi>`_ based on v4.19.113
     - ?
     - ?


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (vX.Y.Z as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No info.

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`Amnesty Kernel for Android 10 <https://forum.xda-developers.com/t/kernel-amnesty.4265411/>`_

Device Specifics
----------------

Guides
^^^^^^

Unlocking the bootloader will permanently trip your device's KNOX status, which will disable Knox-related functionality even if you re-lock your device later.

Since Tab S7 has fastboot mode by default, nothing's need to be done.

To unlock the bootloader enable ``OEM Unlock`` setting in Developer Options of your ROM and proceed in Download mode.

In order to launch download mode, with the device powered off and connected to PC, hold ``Volume Down`` + ``Volume Up``.

In order to launch recovery, with the device powered off, hold ``Volume Up`` + ``Power``.

Developer Info
^^^^^^^^^^^^^^

No strange behavior on non-existent software

Useful Resources
^^^^^^^^^^^^^^^^
