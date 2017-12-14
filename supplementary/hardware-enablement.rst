
Hardware and kernel enablement
==============================

This page is meant as an overview of


* **What Hardware may be inside a smart phone** 
* **Which of those parts need a kernel driver** = probably all
* **What is eachs components current status?** = mainline(since)/wip/blob

**Please be aware that mainlining is A PROCESS** so sometimes "mainline" doesn't mean the same for two chips. However we will use the term in this overview as in "the chip is being mainlined beginning with kernel v.xx) and a detailed overview shall be given on a sub page or an external reference.

How to use this Overview
------------------------

If you are trying to document the parts of a new or incomplete documented device the chips should all be listed in the :doc:`devices/index` and on each devices sub page.

Every hardware part should be listed on this page in it's category (connectivity, sensors, ...) and link to a **detailed sub page** with further info if possible **while only open source status should be presented here**.

Also in the tables below, it would be very useful to know with which kernel version certain drivers were mainline so please try to take the time to **document the kernel version of each's components mainlining success**

Where to find software status
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

How to find all hardware related data is documented on the Devices Overview. However, it's not that trivial to find out if there is an open source (or even mainlined) driver of the specific component. Essentially, you need to search `the linux kernel <https://www.kernel.org/>`_ and drivers should be inside the folder *drivers/*. **Always keep in mind that abbreviations are used** e.g. qcom instead of Qualcomm.

There are many ways to search for specific drivers. I'll need to tinker a little bit or ask around to find out which way works best. All ways shall be listed below


#. You can for example manually browse the mainline kernel by clicking on 'browse' there, then navigate to the 'tree' section and then click yourself through the drivers folder
#. You can search linux kernel mailing lists like `the linux-arm-kernel archives <http://lists.infradead.org/pipermail/linux-arm-kernel/>`_ for specific hardware
#. For **Qualcomm SoCs** there is a community driven `qualcomm mainlining wiki <http://elinux.org/Qualcomm_SOC_Mainlining_Project>`_ as is for **Allwinner** @ `sunxi mainlining <http://linux-sunxi.org/Linux_mainlining_effort>`_
#. You can also look into `kernel changes on kernelnewbies.org <https://kernelnewbies.org/LinuxChanges>`_
#. Wicket from the Maemo community also has a short `list of devices <https://talk.maemo.org/showthread.php?t=99357>`_ and their status pages.

SoC support @ Device Tree Source (dts) folder
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Modern ARM devices should have their own **device tree** inside the mainline kernel. For a really good reference check out `'Device Tree for Dummies' <http://free-electrons.com/pub/conferences/2014/elc/petazzoni-device-tree-dummies/petazzoni-device-tree-dummies.pdf>`_ by Thomas Petazzoni from `Free Electrons <http://free-electrons.com/>`_. Also from Thomas Petazzoni is the great `ARM-soc-checklist <http://elinux.org/images/a/ad/Arm-soc-checklist.pdf>`_ (they really produce stunning docs there)

For all ARM based smart phones and tablets this should be inside 

.. code-block:: guess

   root/arch/arm/boot/dts/

or if your using 64-bit arm64 (e.g. BQ Aquaris M10) all files are sorted by manufacturer inside

.. code-block:: guess

   root/arch/arm64/boot/dts/

System Components
-----------------

System-on-Chips (SoC)
^^^^^^^^^^^^^^^^^^^^^

Device specific dts
~~~~~~~~~~~~~~~~~~~

**Please only include SoCs that are used inside any smart phone/tablet** and have a smart phone/tablet `*.dts` file.

.. list-table::
   :header-rows: 1

   * - Manufacturer
     - SoC
     - Board
     - Mainline(since)
     - file
     - armhf/arm64
   * - Qualcomm
     - APQ8064
     - Asus Nexus 7
     - since 4.6
     - qcom-apq8064-asus-nexus7-flo.dts
     - armhf
   * - Qualcomm
     - APQ8064
     - Sony Xperia yuga
     - ? is inside 4.12-rc2
     - qcom-apq8064-sony-xperia-yuga.dts
     - armhf
   * - Qualcomm
     - MSM8974
     - LG Nexus 5
     - ? inside 4.12-rc2
     - qcom-msm8974-lge-nexus5-hammerhead.dts
     - armhf
   * - Qualcomm
     - MSM8974
     - Sony Xperia Honami
     - ? inside 4.12-rc2
     - qcom-msm8974-sony-xperia-honami.dts
     - armhf


Here, we directly see what is the benefit of these tables -> The Qualcomm MSM8974 SoC is already mainlined and there are several boards one can use as a reference to e.g. **write a fairphone2.dts** with the purpose to one day mainline it! Also, the APQ8064 SoC is used inside Nexus 4 as well...

General dts
~~~~~~~~~~~

Below are gathered mainlined SoCs and Smart phones/Tablets that use it but do not have a device-specific `*.dts` yet.

.. list-table::
   :header-rows: 1

   * - Manufacturer
     - SoC
     - armhf/arm64
     - Smart phones/Tablets
   * - Qualcomm
     - APQ 8060
     - armhf
     - HP TouchPad, HTC Jetstream, HTC Amaze 4G, HTC Vivid, HTC Raider 4G, Le Pan II, LG Nitro HD, Pantech Element, Samsung Galaxy S II X (SGH-T989D), Samsung Galaxy S II LTE, Samsung Galaxy S II Skyrocket, Samsung Galaxy S Blaze 4G, Samsung Galaxy Tab 7.7 LTE, Samsung SGH-i577 Galaxy Exhilarate, Sony Xperia ion
   * - Qualcomm
     - APQ 8064
     - armhf
     - Asus PadFone 2, HTC Droid DNA, HTC J Butterfly, LG Optimus G, Nexus 4, Oppo Find 5, Pantech Vega No.6, Pantech Vega R3, Sharp Aquos Phone Zeta (SH-02E), Sony Xperia UL, Sony Xperia Z, Sony Xperia ZL, Sony Xperia ZR, Xiaomi MI-2, Panasonic P-02E,ZTE Nubia Z5,ZTE Nubia Z5 Mini
   * - Qualcomm
     - APQ 8074
     - armhf
     - ?
   * - Qualcomm
     - APQ 8084
     - armhf
     - Samsung Galaxy S5 LTE-A (Korea), Samsung Galaxy S5+, LG G3 Cat.6, Samsung Galaxy Note 4 LTE, Samsung Galaxy Note Edge, Amazon Fire HDX 8.9, Motorola Moto MAXX, Motorola Droid Turbo, Nexus 6, Inforce IFC6540, Samsung Galaxy Note 4 Duos
   * - Qualcomm
     - MSM 8660
     - armhf
     - HTC Evo 3D (CDMA), HTC Rezound, LG Connect 4G, LG Optimus LTE LU6200, Pantech Vega Racer, Pantech Sky LTE EX, Pantech Burst, LG Lucid, Samsung Galaxy Note, Xiaomi MI-One (CDMA2000 for China Telecom)
   * - Qualcomm
     - MSM 8960
     - armhf
     - Asus Transformer Pad Infinity (3G/4G version), BlackBerry Z10, BlackBerry Classic HTC Droid Incredible 4G LTE, HTC Evo 4G LTE, HTC One X (North America), HTC One XL, HTC Windows Phone 8X, Samsung Ativ S, LG Mach, Motorola Atrix HD, Motorola Droid Razr M, Motorola Droid Razr HD, Motorola Razr HD, Motorola Droid Razr Maxx HD, Nokia Lumia 820, Nokia Lumia 920, Nokia Lumia 925, Nokia Lumia 1020, Panasonic Eluga Power, Qualcomm Snapdragon S4 Plus MSM8960 MDP/S, Samsung Galaxy S III (select versions), Sharp Aquos Phone sv (SH-10D), Sharp Aquos Phone Zeta (SH-09D), Sony Xperia GX, Sony Xperia TL, Sony Xperia SX, Sony Xperia V, Toshiba Regza Phone (T-02D), ZTE Grand Era LTE, ZTE Grand X LTE,[75] ZTE V96, Huawei Ascend P1 LTE, Kyocera Hydro Elite C6750, Nokia Lumia 928, Nokia Lumia 822, Nokia Lumia 810, Sony Xperia T LTE, LG Lucid 2, LG Optimus F7, LG Optimus F5, LG Spectrum 2, LG Optimus VU II, BlackBerry Q10, Huawei Premia 4G, ZTE Vital, ZTE Avid 4G, ZTE Flash, Dell XPS 10, LG Escape, LG Optimus LTE II, Kyocera Hydro XTRM, Kyocera Torque, BlackBerry Porsche Design, Pantech Discover, Pantech Perception, Pantech Flex, Pantech Vega PTL21, Xolo LT900, Kyocera Torque SKT01
   * - Qualcomm
     - MSM 8974
     - armhf
     - ?


Useful sources:


* `Wikipedia list of Qualcomm SoCs with devices using them <https://en.wikipedia.org/wiki/List_of_Qualcomm_Snapdragon_systems-on-chip#Snapdragon_S4>`_
* `Wikipedia list of Tegra SoCs and devices using them <https://en.wikipedia.org/wiki/Tegra>`_

GPU
^^^

There is sadly only a very short list of open source driver projects, mainly `Etnaviv <https://github.com/etnaviv/etna_viv>`_ which is for VIvante GCxxx embedded GPUs and `Freedreno <https://github.com/freedreno/freedreno>`_ for Ardreno GPUs (there was also once lima for mali GPUs, however it seems more or less abandoned, although just recently there was news that someone from AMD is trying to rewrite it as `mesa-lima <https://github.com/yuq/mesa-lima>`_\ ). 

Qualcomm's Adreno
~~~~~~~~~~~~~~~~~


* Adreno 320
* Adreno 330
* Adreno 418

Wireless Connectivity
^^^^^^^^^^^^^^^^^^^^^

WiFi + (x)
~~~~~~~~~~


* Broadcom BCM4339 (inside **mainline** 4.11.2 @ /arch/x86/platform/intel-mid/device_libs/platform_bcm43xx.c also perhabs @/drivers/net/wireless/broadcom/b43)
* Qualcomm QCA6174
* Qualcomm WCN3680 (inside **mainline** 4.11.2 @ /drivers/net/wireless/ath/wcn36xx)
* Qualcomm WCN3680B (inside **mainline** 4.11.2 @ /drivers/net/wireless/ath/wcn36xx)
* Murata SS2908001
* AzureWave AW-NH665
* Qualcomm Atheros WCN3660 (inside **mainline** 4.11.2 @ /drivers/net/wireless/ath/wcn36xx)
* Skyworks SKY85709 

Mobile
~~~~~~


* Qualcomm WTR1605L
* Qualcomm WTR3925
* Avago ACPM7800
* Avago ACPM-7251
* Qualcomm MDM9215M

NFC
~~~


* NXP 65N04
* Broadcom 20793S

Sound
^^^^^

this is probalby located @ /sound/soc/codecs


* Qualcomm WCD9320
* Qualcomm WCD9330
* Qualcomm WCD9310
* Realtek ALC5642 (not inside 4.11.2 but alc5623)

Sensors
^^^^^^^

Touch
~~~~~

probably at /drivers/input and than ../mouse or ../touchscreen


* synaptics e.g has a driver in 4.11.2 @  /drivers/input/mouse 

Orientation & Acceleration
~~~~~~~~~~~~~~~~~~~~~~~~~~

this means gyroscopes, accelerometers, compasses and GPS, probably inside /drivers/iio/


* InvenSense MPU-6515
* Asahi Kasei AK8963
* InvenSense IDG-2020
* ST Microelectronics LSM330DLC
* InvenSense MPU-6050 (inisde **mainline** 4.11.2 @ /include/linux/platform_data_invensense_mpu6050.h & /drivers/iio/imu/inv_mpu6050/)
* Broadcom BCM4751 (general inside **mainline** 4.11.2 @ /arch/mips/bcm47xx/)

Peripherals
^^^^^^^^^^^

Charging & Power Management
~~~~~~~~~~~~~~~~~~~~~~~~~~~


* Texas Instruments BQ51013B
* Texas Instruments BQ24192 (not inside 4.11.2 but similar stuff @ /include/linux/power/)
* Qualcomm PM8921
* Qualcomm PM8821
* Qualcomm PM8941 (inside **mainline** 4.11.2 @ /arch/arm/boot/dts/qcom-pm8941.dtsi & /drivers/input/misc/pm8941-pwrkey.c & /drivers/video/backlight/pm8941-wled.c)
* Qualcomm PM8841 (inside **mainline** 4.11.2 @ /arch/arm/boot/dts/qcom-pm8841.dtsi)
* Qualcomm QFE1100
* Qualcomm PMI8994 (inside **mainline** 4.11.2 @ /arch/arm/boot/dts/qcom/pmi8994.dtsi)
* Qualcomm SMB1358

Slimport
~~~~~~~~


* Analogix Semiconductors ANX7808 e.g. @ mako kernel 3.4: root/drivers/misc/slimport_anx7808 **mainlined** @ 4.11.2: root/drivers/gpu/drm/bridge/

How to test a new kernel
------------------------

There is some `nice documentation <http://www.lieberbiber.de/2015/07/02/hacking-the-bq-part-4-building-and-booting-a-kernel/>`_ by Simon Raffeiner at his blog how to boot a new kernel in Ubuntu Touch (MediaTek devices only!) once for testing. 

.. todo::
  Add info about this on Android/Others
