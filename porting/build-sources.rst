
Build Halium
============

You've got all of your source downloaded, now it's time to start building!

.. _breakfast-and-lunch:

Initialize
----------

First we need to initialize the environment using the envsetup.sh tool. Enter BUILDDIR in a terminal and type::

   source build/envsetup.sh

This will give you an output that looks like this::

    including device/lge/bullhead/vendorsetup.sh
    including vendor/cm/vendorsetup.sh
    including sdk/bash_completion/adb.bash
    including vendor/cm/bash_completion/git.bash
    including vendor/cm/bash_completion/repo.bash

For Halium-5.1
^^^^^^^^^^^^^^

We need to choose the target to build using the lunch command::

   lunch

The output of this command will look something like this::

   You're building on Linux

   Lunch menu... pick a combo:
    1. aosp_arm64-eng   4. aosp_mips-eng     7. cm_bacon-eng
    2. aosp_arm-eng     5. aosp_x86_64-eng   8. cm_bacon-user
    3. aosp_mips64-eng  6. aosp_x86-eng      9. cm_bacon-userdebug

   Which would you like? [aosp_arm-eng]

Here you need to choose your device ``cm_[your device]-userdebug``, for example if you wish to build for the OnePlus One you would type ``cm_bacon-userdebug`` or ``9``.

For Halium-7.1
^^^^^^^^^^^^^^

The ``breakfast`` command is used in LineageOS 14.1 and above (and therefore halium-7.1) to set up the build environment for a specific device. It is easy to use. Simply ensure that you're in BUILDDIR and run the following::

    breakfast [codename]

Breakfast will attempt to find your device, set up all of the environment variables needed for building, and give you a summary at the end. You don't need to worry about any of this, unless it fails.

Modify the kernel configuration
-------------------------------

Halium uses systemd as the init system. This requires various specific kernel configurations.

To check which config options needs to be adjusted we use `mer-kernel-check <https://github.com/mer-hybris/mer-kernel-check>`_ utility provided by mer-hybris::

   git clone https://github.com/mer-hybris/mer-kernel-check
   cd mer-kernel-check
   ./mer_verify_kernel_config <path to kernel configuration>

If you don't know the path to your kernel config run ``grep "TARGET_KERNEL_CONFIG" device/<VENDOR>/<CODENAME>/BoardConfig.mk``. It should be in ``arch/arm/configs/<CONFIG>`` or ``arch/arm64/configs/<CONFIG>`` depending on the architecture of your device.

.. todo::
    Mention that the config parameters CONFIG_IKCONFIG and CONFIG_IKCONFIG_PROC need to be set to y, otherwise Halium wont boot (or add them to the check script

Include your device in fixup-mountpoints
----------------------------------------

Fixup-mountpoints replaces the aliases of block device nodes in ``/dev/block/by-name`` with their literal nodes under ``/dev/block``. This prevents issues caused by ``by-name`` not being populated by systemd.

First check if the codename of your device is already included in the ``<BUILDDIR>/halium/hybris-boot/fixup-mountpoints`` script.

If it's not already included, you will need to add it. Your device should be running LineageOS or another ROM where you can get root access over ADB.

1. Find the fstab file for your device. For my Moto G5 Plus, this was ``fstab.qcom`` in ``device/motorola/potter/rootdir/etc``
2. Enable adb root access
3. Create the skeleton for your device in fixup-mountpoints, right before the ``*)``::

	"[codename]")
            sed -i \
                [replacements, one per line]
                "$@"
            ;;

4. For every line in fstab where the type is not ``auto``, ``emmc`` or ``swap``, run ``readlink -f [src]`` on the target device over ADB. ``[src]`` is the leftmost colum in fstab.
5. Write all of our replacements, one for every mountpoint. Here's the bones of one::

	-e 's [src] [return] ' \

Replace [src] with what you input into readlink and [return] with what it returns.
The space after [return] is important. The build fails without it.

.. note::

    Be careful to ensure that your indentation is the same as other devices! The ``"[codename]")`` line should be indented by four spaces, and everything below it should be indented as shown.

Building the system.img and hybris-boot.img
-------------------------------------------

Halium will use the mkbootimg tool for creating the boot image. In most cases it is not on the local harddisk, so it can be built by issuing::

   mka mkbootimg

To build the ``system.img`` and ``hybris-boot.img`` - required for Halium - use the following commands::

   mka hybris-boot
   mka systemimage

.. note::

    If you use ``make`` and not ``mka`` it is recommended to set ``-j[num]`` to do parallel building, which reduces build time. Replace ``[num]`` with the number of threads in your system plus 2.

If you get any errors, jump down to `Documented errors`_. Otherwise, continue on to `Next steps`_.

Documented errors
-----------------

If you receive errors while building Halium, check the following documents to see if there is a documented solution.

.. toctree::
   :maxdepth: 2

   common-kernel-build-errors
   common-system-build-errors

If your error is not in this list, please :ref:`contact us for help <support-channels>`.

Next steps
----------

Now that you have ``hybris-boot.img`` and ``system.img`` built, let's install them along with the reference rootfs to test functionality.
