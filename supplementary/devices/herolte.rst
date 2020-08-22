
Herolte - Samsung Galaxy S7
===========================

The Samsung Galaxy S7 is a lightweight, powerful handset with an impressively crisp screen, and good look and feel. As with Samsung devices in general, the process of building and flashing ROMs has its peculiarities compared to devices of other makes. This page should help overcome the challenges they might otherwise present.

(Note: This page is still under construction.)

Status
------

Halium
^^^^^^

Halium 7.1 can be built for the Samsung Galaxy S7, although not everything works as of writing.

Building Halium 7.1 for the Galaxy S7 is a straightforward process. It is well described in the UBPorts porting guide and the Halium porting guide, but you should also consult the LineageOS guide. For those wishing undertake this endeavor, some words of advice: 

* Read the guides and familiarize yourself with the process before starting.
* Secure the necessary resources beforehand, including a PC to do the development work on and a good USB cable.
* Download and install the necessary resources before starting.
* Check and record the details of your device (version, hardware, the currently installed OS and its version)
* Completing a successful build is the easy step. Installing, configuring, debugging and fixing issues is the demanding part. However, anyone with a fair amount of patience and the ability to read and follow a slightly above average cooking recipe should manage to build, install and get the system up and running. Making everything work is different question.

For convenience, links to some of the important resources mentioned in the guides are also gathered at the bottom of this page, along with other useful/potentially useful resources not mentioned there.

Good luck!

Distributions
^^^^^^^^^^^^^

The following table is somewhat lacking, but a good start.

.. list-table::
   :header-rows: 1

   * - Distribution
     - Device Specific Files
     - Kernel
     - What works
     - What doesn't work
   * - `LineageOS for Samsung Galaxy S7 wiki page <https://wiki.lineageos.org/devices/herolte>`_
     - `android_device_samsung_herolte <https://github.com/LineageOS/android_device_samsung_herolte/tree/cm-14.1>`_
     - `android_kernel_samsung_universal8890 <https://github.com/ZeroPointEnergy/android_kernel_samsung_universal8890/tree/cm-14.1>`_ based on v3.18.14
     - ?
     - ?
   * - `Halium and Ubports device port page <https://github.com/Halium/projectmanagement/issues/48>`_
     - `Same as above <https://github.com/LineageOS/android_device_samsung_herolte/tree/cm-14.1>`_
     - `android_kernel_samsung_universal8890 <https://github.com/ZeroPointEnergy/android_kernel_samsung_universal8890/tree/cm-14.1>`_ based on v3.18.14
     - Graphics, screen rotation, wifi, lights, sound, vibration.
     - Bluetooth, phone, sms, gps, camera, video.


Kernel & Hardware
^^^^^^^^^^^^^^^^^

Mainline (vX.Y.Z as of writing)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(To be completed...)

Cyanogemod based kernels (LOS & UBP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(To be completed...)

Device Specifics
----------------

Guides
^^^^^^

`Building Lineage OS for the S7 <https://wiki.lineageos.org/devices/herolte/build>`_

`The UBPorts Porting Guide <https://docs.ubports.com/en/latest/porting/introduction.html#>`_

`The Halium Porting Guide <http://docs.halium.org/en/latest/porting/first-steps.html>`_

`Detailed account of one porter's porting process for Ubuntu Touch to the S7, including valuable extra links and tips <https://github.com/Halium/projectmanagement/issues/48#issuecomment-626908532>`_

`Device port discussion thread for the S7 on Github <https://github.com/Halium/projectmanagement/issues/48>`_

Developer Info
^^^^^^^^^^^^^^

In order to flash a custom recovery or boot image, the Samsung Galaxy S7 has to be put into download mode. Simultaneously press the home button, volume-down button and power button until the blue screen appears. Then confirm download mode by pressing the volume-up button.

Switching of the device when in the download mode can be done by simultaneously pressing the volume-down button and the power button until the device switches off.

After flashing a custom recovery, entering custom recovery from the power-off state is done by simulteaneously pressing the volume-up button, the home button and the power button until the Samsung boot logo appears, then IMMEDIATELY releasing all buttons.

If at some point the device does not boot at all from the power off state, no matter how long you press the power button, try this: 

* First enter the download mode as described above. 

* Then switch completely off, also as described above. 

* Now, you should once more be able to either boot normally or boot into recovery, whichever you wish.

Useful Resources
^^^^^^^^^^^^^^^^

`GSMARENA full phone specifications for Samsung Galaxy S7 <https://www.gsmarena.com/samsung_galaxy_s7-7821.php>`_

`Wikipedia entry on Samsung Galaxy S7 <https://en.wikipedia.org/wiki/Samsung_Galaxy_S7>`_

`Firmware for Samsung Galaxy S7 at Sammobile.com <https://www.sammobile.com/samsung/galaxy-s7/firmware/#SM-G930F>`_

`Stock firmware for Galaxy S7 at Firmware Home <https://firmwarehome.com/download/samsung-galaxy-s7-sm-g930f-stock-firmware-download-rom-flash-file/>`_

`TWRP recovery for Samsung Galaxy S7 <https://twrp.me/samsung/samsunggalaxys7.html>`_

`Fix 'kernel is not Seandroid enforcing' problem <https://tricksempire.com/kernel-is-not-seandroid-enforcing-android/>`_

`Videoguide 'kernel is not Seandroid enforcing' problem <https://www.youtube.com/watch?v=cyCileqUVFQ>`_
