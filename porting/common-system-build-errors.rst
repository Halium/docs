Common system build errors
==========================

These are the ``systemimage`` build errors most commonly seen in the Halium community. If you have found and fixed a new error, please document the steps that you have taken to fix it.

signapk.jar missing
-------------------

.. code-block:: guess

    error: 'out/host/linux-x86/framework/signapk.jar', needed by 'out/target/product/kenzo/obj/APPS/TimeService_intermediates/package.apk', missing and no rule to make it

All APKs and Java libraries should be removed from the Makefiles in ``vendor/[manufacturer]/[device]`` and ``device/[manufacturer]/[device]``. The setup script will take care of this for you normally. In case you want to do it manually, simply commenting them out is enough, but you can remove them entirely. An example of these changes can be found at `remove APKs on Lyudmila17/android_device_motorola_athene`_.

Also check the vendor folders of your dependencies.

Undefined or missing bluetooth headers
-------------------------------------

.. code-block:: guess

    *TODO: example*

Some devices requires bluetooth when compiling, which aren't synced for default by Halium. This can be fixed adding LineageOS's repo to the device manifest:

... to the device manifest::

    <project path="system/bt" name="android_system_bt" remote="los" revision="cm-14.1" />
    
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
