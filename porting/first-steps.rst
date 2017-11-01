
First steps
===========

This page contains the first steps you should take to start a Halium port.


Pick an Android target device
-----------------------------

If you're here, you probably already have a device in mind that you wish to port to. However, we still encourage you to port to devices that meet the following requirements:

* **Kernel:** Halium currently requires a device with a kernel greater than or equal to version 3.1.0 - older device kernels are not compatible with the glibc build in the root filesystem being used. Check your device's kernel version by finding "Kernel Version" in the About page of your Android settings.
* **RAM:** While 1GB of RAM is sufficient to start the OS, it is recommended to have greater than 2GB to have a good end user experience.
* **Chipset:** Try to avoid Mediatek chipsets, they are not open-sourced and so there is rarely a usable Android source tree available for them.
* **Storage:** 16GB of storage is generally enough for any Halium-based OS.

Document your target device
---------------------------

Head over to :doc:`/supplementary/how-to-document` to learn about adding your device's information to our device overview. Adding your device will also lead you to looking at other Halium devices, some of which may have similar hardware to yours. You can use fixes made in similar devices to fix your own.

Set up your build device
------------------------

Now you will need to install packages on the computer you wish to build Halium with.

Debian (Stretch or newer) / Ubuntu (16.04 or newer)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are on the ``amd64`` architecture (commonly referred to as 64 bit), enable the usage of the ``i386`` architecture::

   sudo dpkg --add-architecture i386

Install the required dependencies::

   sudo apt install git gnupg flex bison gperf build-essential \
     zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
     libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
     libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \
     python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
     repo liblz4-tool bc

.. todo::
    Add information for installing packages on other distros
