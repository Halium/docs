
Codename - trlte
===========================

Samsung Galaxy Note 4 released October 2014. 3GB of RAM along with active stylus pen. References: `Wikipedia <https://en.wikipedia.org/wiki/Samsung_Galaxy_Note_4>`_ and `GSM Arena <https://www.gsmarena.com/samsung_galaxy_note_4-6434.php>`_.

Status
------

Halium
^^^^^^

  - https://github.com/tyg3rpro/Ubuntu_Touch/blob/master/samsung_trlte.xml
  - https://github.com/tyg3rpro/android_kernel_samsung_trlte
  - https://github.com/tyg3rpro

  - Base Version 7.1

  - Status of working items, in-progess, etc: https://github.com/tyg3rpro/Ubuntu_Touch

Distributions
^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - LineageOS UNOFFICAL
     - https://github.com/tyg3rpro/android_device_samsung_trlte-common
     - https://github.com/tyg3rpro/android_kernel_samsung_trlte
     - seemed ok, not much tested (?)
     - ?
   * - Ubports 
     - TBD
     - TBD
     - GUI, Touchscreen, Power Off Charging Animation, Status LED, Bluetooth (on boot only), some ADB, some Hiemdall
     - QCOM Sensors, Cellular not tested, Media Hub (D-Bus errors), Auto Brightness Sensor, Wifi (forgets pw on reboot), X Cellular, Stylus: shows DMESG/works in libinput but Lormiri ignores, X Audio only shows devices, AppArmor missing items, OTA: partition too small to complete updates


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Kernel (v3.10.4 as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

LineageOS based kernels: 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Please see: https://www.cyanogenmods.org/list-lineage-os-14-1-rom-samsung-phones/#List_of_Available_UNOFFICIAL_LineageOS_141_for_all_Samsung_Phones_and_Tabs_Arranged_Alphabetically

  - Samsung Galaxy NOTE 4 (trltexx) LineageOS 14.1 for Samsung Galaxy NOTE 4
  - Samsung Galaxy NOTE 4 Duos (trlteduos) LineageOS 14.1 for Samsung Galaxy NOTE 4 Duos
  - Samsung Galaxy NOTE 4 Sprint (trltespr) LineageOS 14.1 for Samsung Galaxy NOTE 4 Sprint
  - Samsung Galaxy NOTE 4 T-Mobile (trltetmo) LineageOS 14.1 for Samsung Galaxy NOTE 4 T-Mobile
  - Samsung Galaxy NOTE 4 Verizon (trltevzw) LineageOS 14.1 for Samsung Galaxy NOTE 4 Verizon



Device Specifics
----------------

Guides
^^^^^^

  - Download Boot: Power OFF: Hold PWR + Home button + Volume Down
  - Recovery Boot: Power OFF: Hold PWR + Vol Up until logo boot, release
  - Force Reboot: Hold PWR + Vol Down


Developer Info
^^^^^^^^^^^^^^

  - ADB partially works from Ubuntu
  - some limited Heimdall from /usr/bin from Ubuntu
  - no fastboot
  - no MTP (but Ubuntu will show it mounted).
  - partition/cache no memory left on device for OTA updates.

Useful Resources
^^^^^^^^^^^^^^^^

  - Tyg3rpro's Builds: https://drive.google.com/drive/folders/1CLLNsncJ3ZsCURfXRx7jUByWokBm9Ez6
  - TWRP for trlte: https://dl.twrp.me/trlte/
  - Rooting (if starting from OEM Android): https://forum.xda-developers.com/note-4/help/sm-n910-cf-auto-root-t2897428
  - Phone Case (decent, not quite Unicorn-Beetle tough): https://amzn.to/35srUOq

Other - Not Applicable
^^^^^^^^^^^^^^^^
  For Reference only:
  - LineageOS Official build: Samsung Galaxy Note 4 Exynos (N910C variant): https://github.com/LineageOS/android_device_samsung_treltexx
