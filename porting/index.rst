.. role:: raw-html-m2r(raw)
   :format: html


Porting guide
=============

Device considerations
---------------------


* **Kernel:** Halium currently requires a device with a kernel greater than or equal to version 3.1.0 - older device kernels are not compatible with the glibc build in the root filesystem being used. Check your device's kernel version by using adb with ``uname -a`` for example.
* **RAM:** While 1GB of RAM is sufficient to start the OS, it is recommended to have 2GB at least to have a good end user experience.
* **Chipset:** Try to avoid Mediatek chipsets, they are not open-sourced and so there are nearly no usable Android trees for building available.
* **Flash:** 16GB of flash storage are enough. Most devices have at least this amount of storage.

Setup your environment
----------------------

Setting up your environment is necessary before starting the porting process.

Using Debian (Stretch or newer) or Ubuntu (16.04 LTS or newer)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Step 1: Installing required packages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you are on the ``amd64`` architecture (commonly referred to as 64 bit), enable the usage of the ``i386`` architecture:

.. code-block:: guess

   sudo dpkg --add-architecture i386

Install the required dependencies:

.. code-block:: guess

   sudo apt install git gnupg flex bison gperf build-essential \
     zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
     libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
     libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \
     python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
     repo liblz4-tool bc

What is repo?
"""""""""""""

Repo is a tool written by the Android developers for working on Android source trees. It downloads large numbers of git projects into a repeatable directory structure, important for something as complicated as Android. To do this, Repo uses a manifest, which is simply an XML document that tells it what to get and where to put it. You can find a full reference for the repo command `here <https://source.android.com/source/using-repo.html>`_ here, but we'll mainly be using the repo init and repo sync commands (and repo diff and repo status for analyzing the changes made to the device-specific parts so that its easier later to commit them to a GitHub repo).

**//TODO: Add instructions for installing build tools for other distros as well**

Step 2: Create a new directory to download the Halium tree
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: guess

   mkdir halium && cd halium

This directory will be called BUILDDIR in the remaining part of the guide, when necessary, to avoid confusion.

If the target device has Android 7.1 or LineageOS 14.1 support, it's recommended to select ``halium-7.1``:

.. code-block:: guess

   repo init -u https://github.com/Halium/android -b halium-7.1

If your device does not have Android 7.1 or LineageOS 14.1 support but has support for Android 5.1 or CyanogenMod 12.1, select ``halium-5.1``\ :

.. code-block:: guess

   repo init -u https://github.com/Halium/android -b halium-5.1

**//TODO: Add notes about halium-5.1 and halium-7.1**

``halium-7.1`` is based on LineageOS 14.1
``halium-5.1`` is based on CyanogenMod 12.1

Step 3: Download the source code
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Note:* the repo tool takes some time to download the sources. You need a little patience here. Execute the following:

.. code-block:: guess

   repo sync -c

Specifying ``-c`` only downloads one branch, which makes the download a lot smaller since it won't download all of the old branches, this will also result in a much faster sync time.

You can also specify ``-j[num]`` as it will fetch the files simultaneously. This defaults to 6 consecutive processes but bumping it to 10 makes a big difference on network with high bandwidth.

Prepare the Android tree
------------------------

Put parts together
^^^^^^^^^^^^^^^^^^

Now you need to put all the parts for your device together, and since our tree is based on LineageOS for ``halium-7.1`` or CyanogenMod for ``halium-5.1`` you can use the device files they provide.

Parts that are needed:


* Device tree (e.g. from `LineageOS <https://github.com/LineageOS>`_\ )
* Kernel source (e.g. also from LineageOS)
* Vendor tree (e.g. from `TheMuppets <https://github.com/TheMuppets>`_\ )

LineageOS and TheMuppets have a lot of devices already prepared, but it is not mandatory to use only their sources. Basically any tree capable of producing a working (Android) ROM should suffice.

You might have to check ``lineage.dependencies``\ /\ ``cm.dependencies`` that is included in every LineageOS/CyanogenMod device repo for additional repositories.

Create a local manifest
^^^^^^^^^^^^^^^^^^^^^^^

The repo tool will accept additional repositories to be synced on top of the ones defined by Halium already. Since you are porting for a new device, you also need to do this work. After you have a working configuration your local manifest.xml can go into an issue in the `Halium/projectmanagement repo <https://github.com/Halium/projectmanagement/issues?q=is%3Aissue%20%5Bdevice-port%5D%20in%3Atitle>`_ .

Create additional entries for the repo tool to download the required parts automatically:

.. code-block:: guess

   cd <BUILDDIR>/.repo && mkdir local_manifests && cd local_manifests

Create a new file called ``<VENDOR>_<CODENAME>.xml`` and open it in your favorite editor.

For the time being, add entries to the created xml file as follows:

.. code-block:: guess

   <?xml version="1.0" encoding="UTF-8"?>
   <manifest>
   <!-- Example for a device with one specific vendor repo, and 2 repos for the device, a common and a specific one. At the end, a common kernel repo -->
     <project path="vendor/samsung" name="proprietary_vendor_samsung" remote="them" />
     <project name="android_device_samsung_smdk4412-common" path="device/samsung/smdk4412-common" remote="los" />
     <project name="android_device_samsung_i9300" path="device/samsung/i9300" remote="los" />
     <project name="android_kernel_samsung_smdk4412" path="kernel/samsung/smdk4412" remote="los" />

     <!-- Example for additional repos gathered from the dependencies files in the device or vendor repo -->
     <project name="android_hardware_samsung" path="hardware/samsung" remote="los" />
     <project name="android_external_stlport" path="external/stlport" remote="los" />

   </manifest>

The remote properties "los" and "them" are shortcuts for the already defined remotes that Halium provides. They can be reviewed by looking into default.xml in the .repo/manifests directory (It is also symlinked to .repo/manifest.xml). Depending on which Halium branch you used, default.xml will be either set up for `LineageOS 14.1 <https://github.com/Halium/android/blob/halium-7.1/default.xml>`_ or `CyanogenMod 12.1 <https://github.com/Halium/android/blob/halium-5.1/default.xml>`_. You can create references to new remotes by adding the following snippet in front of any project definition:

.. code-block:: guess

     <remote name="new_remote"
           fetch="http://github.com/<path_to_project>"
           revision="refs/heads/<branchname>" />

It is preferred to add them to your local manifest, and leave the default.xml in its original state.

After your local manifest is finished, you need once again to call the repo tool to download the added parts:

.. code-block:: guess

   repo sync -c

repo will detect most mistakes in your local manifest. Sometimes, if you misspelled an URL for example, you need to tell repo to overwrite already prepared local settings:

.. code-block:: guess

   repo sync -c --force-sync

Modify the kernel configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Halium uses the systemd as the init system which requires various kernel config options to be enabled.

To check which config options needs to be enabled we use `mer-kernel-check <https://github.com/mer-hybris/mer-kernel-check>`_ utility provided by mer-hybris.

.. code-block:: guess

   git clone https://github.com/mer-hybris/mer-kernel-check
   cd mer-kernel-check
   ./mer_verify_kernel_config <path to kernel configuration>

If you don't know the path to your kernel config run ``grep "TARGET_KERNEL_CONFIG" device/<VENDOR>/<CODENAME>/BoardConfig.mk``. It should be in ``arch/arm/configs/<CONFIG>`` or ``arch/arm64/configs/<CONFIG>`` depending on the architecture of your device.

**//TODO: Mention that the config parameters CONFIG_IKCONFIG and CONFIG_IKCONFIG_PROC need to be set to y, otherwise Halium wont boot (or add them to the check script**

Include your device in fixup-mountpoints script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

First check if the codename of your device is already included in the ``<BUILDDIR>/halium/hybris-boot/fixup-mountpoints`` script.

If it's not already included, you will need to add a few lines similar to `following <https://github.com/Halium/hybris-boot/blob/master/fixup-mountpoints#L198-L205>`_ in the ``fixup-mountpoints`` script for all partitions that are mountable (i.e. have an ``fstype`` of ``ext4``\ , ``vfat``\ , ``f2fs`` or others). You can ignore the rest of the partitions.

To figure out the actual device node for the block device you can use following command:

.. code-block:: guess

   readlink -f /dev/block/platform/msm_sdcc.1/by-name/<blockdevicename>

Building
--------

Initialize
^^^^^^^^^^

First we need to initialize the environment using the envsetup.sh tool:

.. code-block:: guess

   source build/envsetup.sh

This will give you an output that looks like this:

.. code-block:: guess

   including device/samsung/maguro/vendorsetup.sh
   including device/samsung/toro/vendorsetup.sh
   including device/samsung/tuna/vendorsetup.sh
   including device/samsung/manta/vendorsetup.sh
   including device/samsung/crespo4g/vendorsetup.sh
   including device/samsung/torospr/vendorsetup.sh
   including device/generic/armv7-a-neon/vendorsetup.sh
   including device/generic/x86/vendorsetup.sh
   including device/oneplus/bacon/vendorsetup.sh
   including device/lge/hammerhead/vendorsetup.sh
   including device/lge/mako/vendorsetup.sh
   including device/asus/tilapia/vendorsetup.sh
   including device/asus/deb/vendorsetup.sh
   including device/asus/flo/vendorsetup.sh
   including device/asus/grouper/vendorsetup.sh

**//TODO: This only works if either in halium-5.1 add_lunch_combo has been executed or in halium-7.1 breakfast has been used, see below comment**

Choose you target
^^^^^^^^^^^^^^^^^

Now we need to choose the target to build using the lunch command:

.. code-block:: guess

   lunch

The output of this command will look something like this:

.. code-block:: guess

   You're building on Linux

   Lunch menu... pick a combo:
    1. aosp_arm64-eng   4. aosp_mips-eng     7. cm_bacon-eng
    2. aosp_arm-eng     5. aosp_x86_64-eng   8. cm_bacon-user
    3. aosp_mips64-eng  6. aosp_x86-eng      9. cm_bacon-userdebug

   Which would you like? [aosp_arm-eng]

Here you need to choose your device ``cm_[your device]-userdebug``\ , example if you were to build the OnePlus One you would choose ``cm_bacon-userdebug`` or ``9``.

**//TODO: LineageOS recommends the breakfast tool instead of lunch.**

Building the system.img and hybris-boot.img
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Halium will use the mkbootimg tool for creating the boot image. In most cases it is not on the local harddisk, so it can be built by issuing

.. code-block:: guess

   mka mkbootimg

To build the ``system.img`` and ``hybris-boot.img`` - required for Halium - use the following commands

.. code-block:: guess

   mka hybris-boot
   mka systemimage

If you use ``make`` and not ``mka`` it's recommended to set ``-j[num]`` to do parallel building, this reduces build time. *NOTE* this is not needed on halium-7.1 since it will calculate parallel building based on CPU performance.

Once you have ``hybris-boot.img`` and ``system.img`` built successfully you can move to testing this on your device.

**//TODO: add testing instructions in this file**

Booting the device
^^^^^^^^^^^^^^^^^^

After you built ``hybris-boot.img`` it is time to test it out.


#. Connect your device with a USB cable to your desktop.
#. Start the device in bootloader (aka "fastboot") mode.\ :raw-html-m2r:`<br>`
   This is usually acomplished by holding some combination of keys on the device for a few seconds. On some devices this is Volume-Down + Power. The Lineage OS wiki is a good resource to check for this.
#. Change to the directory where the boot images have been created with the command ``cout``.
#. Flash the kernel image with: ``fastboot flash boot hybris-boot.img``. You can use ``fastboot boot hybris-boot.img`` to try to boot the kernel image without flashing, but that is not working for some devices.
#. Next reboot into the recovery. You can use the latest version of TWRP recovery to deploy the rootfs and system.img. Please read the :doc:`following guide <deploying-rootfs>` for further information.
#. Once done you can reboot the device.

Debugging
---------

Reading kernel logs
^^^^^^^^^^^^^^^^^^^

To find out what happened during an unsuccessful boot you can check the kernel log files. These can usually be retrieved from ``/proc/last_kmsg`` after rebooting the device into another, working system. A precondition for this is that you have a system that you can successfully boot, such as TWRP.


#. Boot your newly built image
#. Wait for it to fail
#. Reboot the device into the working system.
#. Retrieve the kernel log with ``adb shell cat /proc/last_kmsg > ~/last_kmsg``
#. Read ``~/last_kmsg`` and find out what went wrong

Debugging via telnet
^^^^^^^^^^^^^^^^^^^^

The hybris-boot image can offer you a telnet interface to access the system on the device even if it does not come up fully. To this end, the usb function of the device will be reconfigured to work as a network interface. While bringing this network interface up, the boot image will write a few debug messages. These debug messages are communicated via a clever hack of resetting the serial number of the usb connection. Once you see that the usb networking and telnet have been set up, you can configure the usb networking on your desktop and then telnet into the system.

The steps in detail are:

* Execute this command to watch the changes in the usb serial number:\ :raw-html-m2r:`<br>`
  ``while : ; do lsusb -v 2>/dev/null | grep -Ee 'iSerial +[0-9]+ +[^ ]' ; done | uniq``
* Boot your newly built image
* Watch the output of the lsusb command above. It will put out lines like this:

  .. code-block:: guess

     iSerial                 3 01234567
     iSerial                 3 Mer Debug setting up (DONE_SWITCH=no)
     iSerial                 3 Mer Debug telnet on port 23 on usb0 192.168.2.15 - also running udhcpd

* Determine the name of the usb network device on your desktop:
    ``dmesg | tail``. You're looking for a line similar to this:
  
    .. code-block:: guess

       [ 1234.123456] rndis_host 1-7:1.0 enp0s20f0u7: renamed from usb0

* In this example shown above, ``enp0s20f0u7`` is the usb network device name. Use this for the USBNETWORK below
* Check if the usb network device has a MAC address assigned.

  .. code-block:: guess

     $ ip address show dev USBNETWORK
     6: USBNETWORK: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
      link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff

  If it shows the link/ether address ``00:00:00:00:00:00`` as shown above, you will have to manually assign the MAC address,
 
  .. code-block:: guess

     ip link set USBNETWORK address 02:01:02:03:04:08

  You can set any MAC address you want, it just needs to be a valid MAC address.
* Configure usb networking:

  .. code-block:: guess

     sudo ip address add 192.168.2.1 dev USBNETWORK
     ip address show dev USBNETWORK
     sudo ip route  add 192.168.2.15 dev USBNETWORK
     ping -c 2 192.168.2.15

* Connect with telnet: ``telnet 192.168.2.15``

Now you have terminal access to the system running from initrd.

The ``hybris-boot.img`` brings up the telnet interface if it detects a problem. Alternatively, you can use the ``hybris-recovery.img`` image which will always start telnet.

Porting parts
-------------

.. toctree::

  debug-android-userspace
  graphics
  lights
  vibrator
  wifi
  deploying-rootfs

References
----------

The hybris-boot image is based on work from the Sailfish OS and the `Sailfish Hardware Adaptation Development Kit porting guide <https://sailfishos.org/develop/hadk/>`_ contains valuable tips.
