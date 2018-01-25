
Reading kernel logs
===================

To find out what happened during an unsuccessful boot you can check the kernel log files. These can usually be retrieved from ``/proc/last_kmsg`` after rebooting the device into another, working system. A precondition for this is that you have a system that you can successfully boot, such as TWRP.


#. Boot your newly built image
#. Wait for it to fail
#. Reboot the device into the working system.
#. Retrieve the kernel log with ``adb shell cat /proc/last_kmsg > ~/last_kmsg``
#. Read ``~/last_kmsg`` and find out what went wrong

