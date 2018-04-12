
Reading kernel logs
===================

To find out what happened during an unsuccessful boot you can check the kernel log files. These can usually be retrieved after rebooting the device into another, working system. Generally, your recovery image will be the "working system".

Linux kernel <=3.4
------------------

Until Kernel 3.4, Android developers created a driver that the Linux kernel may use to store its kernel message buffer in a special persistent location in RAM. This information is preserved over a reboot but not a hard power cycle (such as holding the power button or powering off). This location is preserved to the system in ``/proc/last_kmsg``

To use ``last_kmsg`` to debug problems in your port, do the following:

#. Boot your newly built image
#. Wait for it to fail
#. Reboot the device into a working system.
#. Retrieve the kernel log with ``adb shell cat /proc/last_kmsg > ~/last_kmsg``
#. Read ``~/last_kmsg`` and find out what went wrong

If you aren't able to find these files, ensure that the following configs are set in your kernel config::

    CONFIG_ANDROID_RAM_CONSOLE=y
    CONFIG_ANDROID_RAM_CONSOLE_ENABLE_VERBOSE=y

Linux Kernel >3.4
-----------------

After Kernel 3.4, most Android vendors have used the upstream ``pstore`` and ``ramoops`` drivers to store kernel logs after a panic.

You can get these logs by following these steps:

#. Boot your newly built image
#. Wait for it to fail
#. Reboot the device into a working system.
#. Find and retrieve the logs from ``/sys/fs/pstore/console-ramoops``. The file may be named slightly differently, but will be in this directory.

If you aren't able to find these files, ensure that the following configs are set in your kernel config::

    CONFIG_PSTORE=y
    CONFIG_PSTORE_CONSOLE=y
    CONFIG_PSTORE_PMSG=y
    CONFIG_PSTORE_RAM=y

Most devices require that the kernel panics in order to offer these logs. You can cause a kernel panic by running these commands as root:

.. warning::

    Yes, these commands really do cause a kernel panic. Don't run them on your production machine.

.. code-block:: shell

    echo 1 > /proc/sys/kernel/sysrq
    echo c > /proc/sysrq-trigger


