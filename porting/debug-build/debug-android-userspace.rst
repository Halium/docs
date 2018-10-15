
Debugging the Android userspace
===============================

Debugging the Android userspace

lxc-android
-----------
lxc-android is the container in which the Android userspace is running. You can check that it is started with the following command::

    systemctl status lxc@android

LXC needs some kernel config to make sure it runs correctly. Check that you have all the needed options by running the following command on the device::

    lxc-checkconfig

All option except ``User namespace`` need to be the green word `enabled`. If one of the options is a yellow `missing` or a red `required`, then you need to change the kernel config, rebuild hybris-boot and check the status again.

.. note::

    I was getting the following error, which I didn't understand:
    ``lxc-start: utils.c: mkdir_p: 254 Invalid argument - failed to create directory '/sys/fs/cgroup/net_cls//lxc/android'``
    It appears like LXC is expecting some functionality that doesn't work yet in Linux 3.4. Counter-intuitively I had to disable the following functionalities in the defconfig to make it work::

        CONFIG_NET_CLS_CGROUP=n
        CONFIG_NETPRIO_CGROUP=n

.. _logcat:

Logcat
------

Logcat is a tool that reads the Android user space logs. This includes all services that should be running in Halium. You can run it at any time with the following command::

   /system/bin/logcat

For radio (Wi-Fi, GSM, LTE) logs, you can add a flag::

   /system/bin/logcat -b radio

If you're not able to run this command for any reason (for example, because you're running an armhf rootfs on an arm64 device), you can try to run it inside the Android container via ``lxc-attach``::

    lxc-attach -n android -- /system/bin/logcat

You may similarly use this to run any binary inside the Android system. Simply replace the command after the two dashes.

dmesg
-----

Even though Android logs do not normally end up in dmesg, early initialization of Android and kernel output ends up here::

   dmesg

strace
------

For cases where the log files do not reveal sufficient detail, a ``strace`` can be helpful. This is how you get a strace for the example of ``test_hwcomposer``::

   EGL_PLATFORM=hwcomposer strace test_hwcomposer

backtrace
---------

Another debugging technique is to investigate the backtrace when a program crashes. This is how you get a backtrace for the example of ``test_hwcomposer``::

   EGL_PLATFORM=hwcomposer gdb test_hwcomposer

This will start the interactive debugger ``gdb``. At the prompt of ``gdb`` you enter ``run``. Now the program is executed and you wait for it to crash. Then you enter ``bt full``. This will give you the full backtrace of what the program was trying to execute at the moment of the crash.

In order to make the backtrace most useful you want to ensure that you have debug symbols installed for the program you are debugging.

Firstly, let's fix the ``PATH`` variable which is currently missing ``/sbin`` on the reference rootfs::

   export PATH=$PATH:/sbin

Secondly, do install debug symbols for libc::

   apt install libc6-dbg

Thirdly, install whichever package contains the debug symbols for the program in question. Typically it is in a package with a name similar to the one containing the program and ending in ``-dbg``. For the example of ``test_hwcomposer`` you want::

   apt install libhybris-dbgsym

If ``gdb`` reports "(no debugging symbols found)", then you are still missing debug symbols, look further for the relevant package.

.. todo::

    Document how to deal with firmware partitions.

    For example xLeEco Le Max2, codename "x2" has a firmware partition where the vendor blobs are stored. Initially lxc@android would not start. The resolution was roughly:

    * no need for a vendor blobs repository in the manifest
    * determine firmware partition name
    * ensure fix-mountpoints takes it into account
    * reflash android to ensure the blobs are in the partition
    * reflash halium

    See http://logs.nslu2-linux.org/livelogs/halium/halium.20180430.txt
