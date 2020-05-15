
First steps
===========

This page contains the first steps you should take to start a Halium port.

.. _support-channels:

Getting help
------------

If you get stuck at any point during the porting process, we're here to help! You can contact us via the following support channels:

* IRC: #halium on Freenode
* Matrix: #halium:matrix.org
* Telegram: @halium

When you contact us, please use a pastebin service like `pastebin.com <https://pastebin.com>`_ to **pastebin the full log** of whichever step you are at. Also please point out which section of the documentation you're stuck on.

Pick an Android target device
-----------------------------

If you're here, you probably already have a device in mind that you wish to port to. However, we still encourage you to port to devices that meet the following requirements:

Source availability
    Your device must have its Linux kernel source publicly available. The source code required to build LineageOS 12.1 or 14.1 must also be available. Both of these should be available if your device has a LineageOS 12.1 or 14.1 port, or a port of a LineageOS derivative based on these versions.
Kernel
    Halium currently requires a device with a Linux kernel version greater than or equal to 3.10.0. According to the `systemd v217 README <https://github.com/systemd/systemd/blob/v217/README#L40>`_, older device kernels are not compatible with systemd v217 or newer. You may learn your device's kernel version by finding "Kernel Version" in the About page of your Android settings. The kernel version can also be found in the ``Makefile`` at the top level of any Linux kernel source tree.

    Some Halium distributions may use a kernel as old as 3.4, such as Ubuntu Touch.
RAM
    1GB of RAM is sufficient to start most Halium distributions. 2GB or higher is recommended for a better end-user experience.
Storage
    16GB of storage is required. Devices with less storage will likely not have enough space for a full Halium distribution.

It is unlikely that you will be able to build and run Halium if your device does not meet these requirements. Please :ref:`contact us <support-channels>` if you are unsure whether your device meets these requirements.

Collaborate
-----------

Head over to the  `list of ports <https://github.com/Halium/projectmanagement/issues>`_ and check if someone is already working on this device. If it is started, collaborate with those porters.

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

Update your package lists to take advantage of the new architecture::

    sudo apt update

Install the required dependencies::

   sudo apt install git gnupg flex bison gperf build-essential \
     zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
     libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
     libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \
     python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
     repo liblz4-tool bc lzop imagemagick libncurses5 rsync

Arch
^^^^

If you have an ``amd64`` installation of Arch, you need to add the ``[multilib]`` repository to your ``/etc/pacman.conf`` . This will allow you to install and run ``i686`` packages. Please refer to `'Official Repositories/multilib' on the Arch Wiki <https://wiki.archlinux.org/index.php/multilib>`_.

Install the ``base-devel`` package if you have not already.

Install the required dependencies from AUR::

   git clone https://aur.archlinux.org/halium-devel.git && cd halium-devel && makepkg -i

.. Note::
    Arch uses Python 3 as its default ``python``, which may cause some errors while building. Using a Python 2 virtualenv is highly recommended. Please refer to `'Python/Virtual environment' on the Arch Wiki <https://wiki.archlinux.org/index.php/Python/Virtual_environment>`_ for instructions on setting up a Virtual Environment.
