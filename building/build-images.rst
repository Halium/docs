
Building Halium images
======================

A Halium build consists of two images, a boot image containing the initramfs
and a system image containing a minimal android that will be executed in an LXC
container. In this section we want to build them using an exsiting Halium port.
See the :doc:`/supplementary/devices/index` to pick one of the supported devices.

Cloning the Halium base tree
----------------------------

Make yourself a new directory to put your Halium source in::

   mkdir halium && cd halium

The next step is to initialize the Halium tree, for that you need your device's
supported Halium version (currently ``halium-7.1`` or ``halium-5.1``). Look the
version up and replace ``halium-X.X`` with it in the following command, then
execute it::

   repo init -u https://github.com/Halium/android -b halium-X.X --depth=1

After that we need to clone all repositories, which are about 4 GiB::

   repo sync -c

Downloading device specific repositories
----------------------------------------

We currently only have got the base tree, now we need to download all device
specific repositories (replace DEVICE with your device's codename)::

   ./halium/devices/setup DEVICE

This will add the needed repositories to repo and sync everything.

Build the images
----------------

So that we have got all repositories needed to build Halium for your device, we
can set up the build environment and configure it for our device

On ``halium-7.1`` or later do::

   source build/envsetup.sh
   breakfast DEVICE eng

And on ``halium-5.1`` do::

   source build/envsetup.sh
   lunch cm_DEVICE-eng

The last step is to start the build of ``hybris-boot``, the ``systemimage`` and
``mkbootimg`` which is a host dependency::

   mka mkbootimg
   mka hybris-boot
   mka systemimage

This will take some time, so better go and grab a coffee.
