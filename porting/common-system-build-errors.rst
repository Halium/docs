Common system build errors
==========================

These are the ``systemimage`` build errors most commonly seen in the Halium community. If you have found and fixed a new error, please document the steps that you have taken to fix it.

signapk.jar missing
-------------------

.. code-block:: guess

    error: 'out/host/linux-x86/framework/signapk.jar', needed by 'out/target/product/kenzo/obj/APPS/TimeService_intermediates/package.apk', missing and no rule to make it

Remove all APKs and Java libraries from the Makefiles in ``vendor/[manufacturer]/[device]`` and ``device/[manufacturer]/[device]``. Simply commenting them out is enough, but you can remove them entirely. An example of these changes can be found at `remove APKs on Lyudmila17/android_device_motorola_athene`_.

Also check the vendor folders of your dependencies.

HYBRIS_BOOT_PART and HYBRIS_DATA_PART
-------------------------------------

.. code-block:: guess

   find: ‘device/*/generic’: No such file or directory
   find: ‘device/unknown’: No such file or directory
   find: ‘device/android’: No such file or directory
   halium/hybris-boot/Android.mk:67: ********************* /boot appears to live on ERROR: *fstab* not found
   halium/hybris-boot/Android.mk:68: ********************* /data appears to live on ERROR: *fstab* not found
   halium/hybris-boot/Android.mk:71: *** There should be a one and only one device entry for HYBRIS_BOOT_PART and HYBRIS_DATA_PART.

Make sure you run the commands :ref:`here <breakfast-and-lunch>` before trying to build.


.. _remove apks on lyudmila17/android_device_motorola_athene: https://github.com/Lyudmila17/android_device_motorola_athene/commit/a752422012165d937c058c1b671497bad44a4962