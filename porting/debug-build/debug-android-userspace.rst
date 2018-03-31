
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

Debug Libhybris crash
---------------------

One of the main problems with the current Hybris based architecture, is the lack of symbols resolution and mapping once a crash happens at the Android layer. To workaround this we need to manuly import non stripped libaries

.. todo::

    Add information for importing debug libhybris libraries.
