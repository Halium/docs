
Debugging the Android userspace
===============================

Debugging the Android userspace

Logcat
------

Logcat is a tool that reads the Android userspace logs. This includes all services that should be running in Halium. You can run it at any time with the following command::

   /system/bin/logcat

For radio (Wi-Fi, GSM, LTE) logs, you can add a flag::

   /system/bin/logcat -b radio

dmesg
-----

Even though Android logs does not normally end up in dmesg, early initialization of Android and kernel output ends up here::

   dmesg

Debug Libhybris crash
---------------------

One of the main problems with the current Hybris based architecture, is the lack of symbols resolution and mapping once a crash happens at the Android layer. To workaround this we need to manuly import non stripped libaries

.. todo::

    Add information for importing debug libhybris libraries.