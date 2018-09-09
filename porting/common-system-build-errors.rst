Common system build errors
==========================

These are the ``systemimage`` build errors most commonly seen in the Halium community. If you have found and fixed a new error, please document the steps that you have taken to fix it.

signapk.jar missing
-------------------

.. code-block:: guess

    error: 'out/host/linux-x86/framework/signapk.jar', needed by 'out/target/product/kenzo/obj/APPS/TimeService_intermediates/package.apk', missing and no rule to make it

All APKs and Java libraries should be removed from the Makefiles in ``vendor/[manufacturer]/[device]`` and ``device/[manufacturer]/[device]``. The setup script will take care of this for you normally. In case you want to do it manually, simply commenting them out is enough, but you can remove them entirely. An example of these changes can be found at `remove APKs on Lyudmila17/android_device_motorola_athene`_.

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

Flex errors
-----------

.. code-block:: guess

   [ 7% 1622/20905] Lex: libsepol_32 <= external/selinux/libsepol/cil/src/cil_lexer.l 
   FAILED: /bin/bash -c "prebuilts/misc/linux-x86/flex/flex-2.5.39 -o/home/mika/halium/out/host/linux-x86/obj32/SHARED_LIBRARIES/libsepol_intermediates/cil/src/cil_lexer.c
   external/selinux/libsepol/cil/src/cil_lexer.l" flex-2.5.39: loadlocale.c:130: _nl_intern_locale_data: Assertion `cnt < (sizeof (_nl_value_type_LC_TIME) / sizeof (_nl_value_type_

Run ``cp /usr/bin/flex halium/prebuilts/misc/linux-x86/flex/flex-2.5.39``
