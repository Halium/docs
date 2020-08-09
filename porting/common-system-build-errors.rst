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
--------------------------------------

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

Make sure you run the commands :ref:`here <breakfast-and-lunch>` before trying to build. The Makefile depends on the environment set up immediately before by envsetup.sh; so if running in a build environment such as Emacs, be sure to set your compile command to something like "source build/envsetup.sh && breakfast [codename] && make [target]"


.. _remove apks on lyudmila17/android_device_motorola_athene: https://github.com/Lyudmila17/android_device_motorola_athene/commit/a752422012165d937c058c1b671497bad44a4962

Flex locale error
-----------------

.. code-block:: guess

   [ 19% 2365/12156] Lex: checkpolicy <= external/selinux/libsepol/cil/src/cil_lexer.l
   FAILED: /bin/bash -c "prebuilts/misc/linux-x86/flex/flex-2.5.39 -o/home/peter/docs/devel/halium.amami/out/host/linux-x86/obj/STATIC_LIBRARIES/libsepol_intermediates/cil/src/cil_lexer.c external/selinux/libsepol/cil/src/cil_lexer.l"
   flex-2.5.39: loadlocale.c:130: _nl_intern_locale_data: Assertion `cnt < (sizeof (_nl_value_type_LC_TIME) / sizeof (_nl_value_type_LC_TIME[0]))' failed.
   Aborted (core dumped)

This seems to be a problem with locales and the prebuilt ``flex``. You can avoid this by using the flex installed on your host::

    export USE_HOST_LEX=yes
    make systemimage

Missing bison error
-------------------

.. code-block:: guess

    [  1% 322/20069] Yacc: checkpolicy <= external/selinux/checkpolicy/policy_parse.y
    FAILED: /bin/bash -c "prebuilts/misc/linux-x86/bison/bison -d -v --defines=/home/builder/workdir/out/host/linux-x86/obj/EXECUTABLES/checkpolicy_intermediates/policy_parse.h -o /home/builder/workdir/out/host/linux-x86/obj/EXECUTABLES/checkpolicy_intermediates/policy_parse.c external/selinux/checkpolicy/policy_parse.y"
    /bin/bash: prebuilts/misc/linux-x86/bison/bison: No such file or directory

The error message is very misleading here. The issue stems from the bison shipped with ``halium-7.1`` at ``prebuilts/misc/linux-x86/bison/bison`` being 32-bit only, with the host system lacking 32-bit compatibility.

The fix is to install 32-bit support for Ubuntu via:

.. code-block:: guess

    sudo dpkg --add-architecture i386
    sudo apt-get update
    sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386
