
laurel_sprout - Xiaomi Mi A3
============================  

.. list-table::
   :header-rows: 0

   * - Codename
     - laurel_sprout 
   * - Halium status
     - Halium 9 (WIP)
   * - Kernel
     - v4.14.7
   * - SoC
     - Qualcomm SDM665 Snapdragon 665
   * - CPU
     - Octa-core 4x2.0 GHz Kryo 260 Gold & 4x1.8 GHz Kryo 260 Silver
   * - GPU
     - Adreno 610
   * - RAM
     - 4 GB
   * - Storage
     - 64 GB / 128 GB
   * - Connectivity
     - Wi-Fi, Bluetooth 5.0,
   * - Camera Front
     - 32 MP, No flash
   * - Camera Back
     - 48 MP + 8 MP + 2 MP, LED flash
   * - Battery
     - Non removable 4030mAh
   * - Sound
     - Speaker, Microphone, 3.5mm Headphone Jack
   * - Touch screen
     - 6.088 inch HD+ Super AMOLED capacitive touchscreen,
   * - Display
     - 720 x 1560 pixels, ~286 ppi, 16M colors
   * - Navigation
     - GPS, A-GPS, GLONASS, BDS
   * - Sensors
     - Ambient Light Sensor, Accelerometer, Proximity, Gyroscope
   * - Other
     - IR Blaster
   * - Connector
     - 2.0, Type-C 1.0 reversible connector
   * - Quick Charge support 
     - 18W quick charging via Qualcomm Quick Charge 3.0. 
   * - Initial Android Version 	
     - Android 9.0 "Pie"
   * - Latest Android Version 	
     - Android 11

Status
------

Halium
^^^^^^

A port for Halium 9 is Work-in-Progress by `mintphin <https://github.com/mintphin>`_ . The device is capable of running Ubuntu touch based on erfan's GSI images.
The latest erfan's GSI images are based on Ubuntu touch OTA-13.

Distributions
^^^^^^^^^^^^^


.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `Ubuntu Touch <https://devices.ubuntu-touch.io/device/laurel-sprout>`_
     - Not available
     - `source <https://github.com/mintphin/lunecrash>`_ based on v4.14.7
     - refer device specific `page <https://devices.ubuntu-touch.io/device/laurel-sprout>`_ 
     - refer device specific `page <https://devices.ubuntu-touch.io/device/laurel-sprout>`_ 
   * - LineageOS placeholder `device page placeholder <placeholder>`_
     - `android_device_placeholder <placeholder>`_
     - `android_kernel_placeholder <placeholder>`_ based on vX.Y.Z
     - ?
     - ?
   


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (vX.Y.Z as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Write whether something that is needed for the device is mainline already (switch the version in the heading for what's recent when you write this). This means **device tree source files (.dts) as well as single drivers** (for example only the wifi driver).

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If other kernels exist, just make up headlines with a name that describe the origin (Cyanogemod, LineageOS, UBports, Canonical, ...) and which is the underlying mainline version. Afterwards describe what's been improved or altered and if possible why or what is still missing.

Device Specifics
----------------

Guides
^^^^^^

This should be populated with guides how to get into different boot modes and similar. Maybe this can be pulled from the `LOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_.

Developer Info
^^^^^^^^^^^^^^

Some devices show strange behaviour of some kind, try to find this (for example in the xda-developers forum) and document it

Useful Resources
^^^^^^^^^^^^^^^^

If anything might be usefull but didn't fit above you can just throw in some links here.
