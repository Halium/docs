
Reading kernel logs
===================

To find out what happened during an unsuccessful boot you can check the kernel log files. These can usually be retrieved from ``/proc/last_kmsg`` after rebooting the device into another, working system. 
TWRP or some other recovery is suggested here as that other system. Alternatively you could use the halium-boot init in telnet access.

#. Boot your newly built image
#. Wait for it to fail
#. Reboot the device into the working system.
#. Retrieve the kernel log with ``adb shell cat /proc/last_kmsg > ~/last_kmsg``
#. Read ``~/last_kmsg`` and find out what went wrong

.. note::

   Make sure you do not power the device off and on again. It must be a reboot in order to keep the contents of the ram and therefore the log. 

.. note::

   If you can't get the log file, double check that you have the two necessary configs:
   
   CONFIG_ANDROID_RAM_CONSOLE=y
   CONFIG_ANDROID_RAM_CONSOLE_ENABLE_VERBOSE=y
   
   Some porters report that they still cannot get the logs to work. Your milage may vary. 
   
.. todo::

    Newer kernels do not have ``/proc/last_kmsg`` but instead ``/sys/fs/pstore/console-ramoops``. Or is it ``/sys/fs/pstore/console-ramoops-0``? 


