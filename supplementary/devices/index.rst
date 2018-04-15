Device Overview
===============

These pages detail devices that


* ( A ) **have a running Halium Image**
* ( B ) **had a Halium image in the past**
* ( C ) **users want to see ported**

All of these should only be document in the exact same way here and **only an overview shall be given on this page** everything that goes into more detail should please be posted on a device specific sub page!

.. toctree::
   :maxdepth: 1
   
   devicetemplate
   dream2lte
   bullhead
   cedric
   chaozu
   deb
   flo
   fp2
   hammerhead
   krillin
   mako
   oneplus3
   pme
   T00F
   titan
   vegeta
   wt88047
   yuga
   taoshan
   Z00L
   

How to document
---------------

Purpose
^^^^^^^

This table is meant for 2 purposes:


* (A) give porters a **quick status reference** what has already been done in regard of Halium to a specific device or what the starting conditions are
* (B) make hardware visible for **kernel team** to see there may be a possibility of **a common drivers base** for multiple devices

Table Format
^^^^^^^^^^^^

Please use the following where the formatting is not obvious:


#. First Row 'Device' is Manufacturer + Device Name and **links to the devices sub page**
#. Second Row 'Codename' is the official Codename as stated inside the Android/Ubuntu Touch/Lineage sources
#. Third Row  'Halium status' is a very short description like 'working fully' or 'boot loop' with the base version attached so e.g. with halium 5.1 base: 'working fully - 5.1'
#. All following Hardware Rows **should link to a detail page about every chip**
#. If you **only have the labels from chips available** just set them inside 'label' perhaps someone else knows more details (most common for cameras, see Nexus 4 example below)
#. **Kernel Version Please fill this one only when there is an existing Halium image!**

Getting the Info
^^^^^^^^^^^^^^^^


* Search **Wikipedia** for your device, a good starting points are the articles that compare `smart phones <https://en.wikipedia.org/wiki/Comparison_of_smart phones>`_ or `tablets <https://en.wikipedia.org/wiki/Comparison_of_tablet_computers>`_
* Search the `xda-developers forum <https://forum.xda-developers.com>`_
* Connect to your device via adb (assuming you have some kind of Android on your phone/tablet) and search for infos using getprop or similar
* Search for **teardowns** and scan the images for readable chips and try to find out what each one does (you may of course do a teardown on your own) good starting points for this are iFixit or Youtube Videos that show how to repair/tear down a device
* Search the `LineageOS device database <https://github.com/LineageOS/lineage_wiki/tree/master/_data/devices>`_ for your devices codename.
* Please **write down your sources somewhere and link to them below the table or in the device's sub page**

Devices
-------

.. list-table::
   :header-rows: 1

   * - Device
     - Codename
     - Halium status
     - Kernel
     - SoC
     - CPU
     - GPU
     - RAM
     - Storage
     - Connectivity
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Other
   * - Oneplus 5
     - cheeseburger
     - Halium porting started
     - ?
     - Qualcomm Snapdragon 835
     - CPU
     - Qualcomm Adreno 540
     - 8 Gb LPDDR4
     - Storage
     - Connectivity
     - Sony IMX 371
     - Dual Camera with Sony IMX398 (wide angle) + Sony Exmor IMX350 ("telephoto")
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Other
   * - :doc:`Samsung Galaxy S8+ <dream2lte>`
     - dream2lte
     - Halium 7.1 WIP
     - v4.4.79
     - Samsung Exynos 9 Octa 8895
     - 4x 2.3 GHz Exynos M2 Mongoose, 4x 1.7 GHz ARM Cortex-A53
     - Mali-G71 MP20
     - Samsung K3UH5H50MM-NGCJ 4 GB LPDDR4
     - Toshiba THGAF4G9N4LBAIR 64 GB UFS (NAND flash + controller)
     - Qualcomm WTR5975 (RF transceiver), Murata KM7118064 (WiFi), NXP 80T71 (NFC)
     - Sony IMX320 Exmor RS (8MP)
     - Sony IMX333 Exmor RS (12MP)
     - Battery @ 3.85V, 3500 mAh
     - Qualcomm WCD9341 (audio codec)
     - Touch screen **??**
     - Super AMOLED (1440x2960)
     - GPS, A-GPS, GLONASS, BDS, GALILEO
     - Proximity, Light, Accelerometer, Compass, Gyroscope, Barometer, Fingerprint, Hall, Heart rate
     - Skyworks 78160-11 (?), Avago AFEM-9066 (?), Avago AFEM-9053 (?), Silicon Mitus SM5720 (Power Management), Qualcomm PM8998 (Power Management)
   * - Samsung Galaxy S8
     - dreamlte
     - No work so far
     - v4.4.79
     - Samsung Exynos 9 Octa 8895
     - 4x 2.3 GHz Exynos M2 Mongoose, 4x 1.7 GHz ARM Cortex-A53
     - Mali-G71 MP20
     - Samsung K3UH5H50MM-NGCJ 4 GB LPDDR4
     - Toshiba THGBF7G9L4LBATR 64 GB UFS (NAND flash + controller)
     - Qualcomm WTR5975 (RF transceiver), Murata KM6D28040 (WiFi), NXP 80T71 (NFC)
     - Sony IMX320 Exmor RS (8MP)
     - Sony IMX333 Exmor RS (12MP)
     - Battery @ 3.85V, 3000 mAh
     - Qualcomm WCD9341 (audio codec)
     - Touch screen **??**
     - Super AMOLED (1440x2960)
     - GPS, A-GPS, GLONASS, BDS, GALILEO
     - Proximity, Light, Accelerometer, Compass, Gyroscope, Barometer, Fingerprint, Hall, Heart rate
     - Skyworks 78160-11 (?), Avago AFEM-9066 (?), Avago AFEM-9053 (?), Silicon Mitus SM5720 (Power Management), Qualcomm PM8998 (Power Management), IDT P9320S (?), Maxim MAX77838 (Power Management)
   * - :doc:`LG Nexus 5 <hammerhead>`
     - hammerhead
     - ? reference
     - ?
     - Qualcomm Snapdragon 800
     - Krait 400 @ 4 x 2.5 GHz
     - Qualcomm Adreno 330
     - SK Hynix H9CKNNNBPTMRLR-NTM 2 GB LPDDR3-1600 RAM
     - Sandisk SDIN8DE4 16 GB NAND flash (15 GB version)
     - Qualcomm WTR1605L (LTE/HSPA+/CDMA2K/TDSCDMA/EDGE/GPS transceiver), Broadcom BCM4339 (5G & WiFi), Avago ACPM-7600 (RF power amp), Qualcomm QFE1100 (RF enevlope tracking amp)
     - Cam Front
     - Cam back
     - LG BL-T9 @ 3.8V, 2300 mAh
     - Qualcomm WCD9320
     - Touch Screen +  Synaptics S3350B (Controller)
     - Display
     - Navigation
     - InvenSense MPU-6515 (6-Axis Gyro + Acc), Asahi Kasei AK8963 (3-Axis compass), InvenSense IDG-2020 (2-Axis Gyro - for OIS)
     - Avago RFI335 (optocopler ?), Qualcomm PM8841 & PM8941 (power management), Analogix ANX7808 (Slimport transmitter), Texas Instruments BQ24192 (I2C controlled USB charger)
   * - :doc:`Nexus 5X <bullhead>`
     - bullhead
     - ? reference
     - ?
     - Qualcomm Snapdragon 808 (MSM8992)
     - CPU
     - Qualcomm Adreno 418
     - Samsung K3QF3F30BM-QGCF 2 GB LPDDR3 RAM
     - Toshiba THGBMFG7C2LBAIL 16 GB eMMC
     - Qualcomm WTR3925 (LTE Transceiver), Skyworks 77814-11(LTE power amp), Avago ACPM7800 (GSM/Edge power amp), Qualcomm QCA6174 (WiFi), NXP PN548 (NFC), RF Micro Devices RF1149A (RF), Qualcomm QFE1100 (RF enevlope tracking)
     - Cam front
     - Sony IMX377 12.3 MP (sensor)
     - LG BL-T19 @ 3.8V, 2700 mAh
     - Qualcomm WCD9330
     - Touch
     - Display
     - Nav
     - Sens
     - Qualcomm SMB1358(Quick Charge), Qualcomm PMI8994 (Power management), ST Microelectronics STM32F411CE (32-bit 100 MHz ARM Cortex-M4 RISC microcontroller), Avago BFI523(?)
   * - Oneplus One
     - bacon
     - ? reference
     - ?
     - Qualcomm Snapdragon 801 (MSM8974PRO-AC r2p1)
     - Krait 400 @ 4 x 2.5 GHz
     - Qualcomm Adreno 330
     - Samsung K3QF7F70DM-QGCF 3 GB LPDDR3
     - Toshiba THGBMBG9D8KBAIG eMMC 5.0 64 GB
     - Skyworks SKY85709 (WiFi), Qualcomm WCN3680 (WiFi, Bluetooth, FM), Qualcomm WTR1625L (RF transceiver)
     - P5V35A Sunny Optical Technology
     - P13N05A Sunny Optical Technology with Sony Exmor IMX 214(sensor)
     - Oneplus BLP571 @ 3.8V, 3100 mAh
     - Qualcomm WCD9320
     - Synaptics S3508A(controller)
     - display
     - navi
     - AGD2 2402 WX9DR(gyro?)
     - Qualcomm PM8941 + PM8841(power management), Skyworks SKY77629-21(power amp)
   * - :doc:`Fairphone 2 <fp2>`
     - fp2
     - -
     - -
     - Qualcomm Snapdragon 801 (MSM8974AB-AB)
     - Krait 400 (?) @ 4 x 2.5 GHz
     - Qualcomm Adreno 330
     - Samsung K3QF2F20EM 2 GB LPDDR3 RAM
     - Samsung KLMBG4WEBC 32 GB eMMC NAND
     - Qualcomm WCN3680B (WiFi + Bluetooth), Qualcomm WTR1625L (RF Receiver), RF Micro Device RF7389EU (RF amp)
     - Camera Front
     - Camera Back
     - ? @ 3.8 V, 2420 mAh
     - Qualcomm WCD9320
     - Touch screen
     - Display
     - Navigation
     - ST Microelectronics LSM330DLC 6-Axis (Gyro + Acc)
     - Qualcomm QFE1100 (Power Management), Qualcomm PM8841 (Power Management IC)
   * - :doc:`LG Nexus 4 <mako>`
     - mako
     - -
     - -
     - Qualcomm Snapdragon S4 Pro (APQ8064)
     - Krait 300 (ARMv7) Quad core @ 1.5 GHz
     - Qualcomm Adreno 320
     - Samsung K3PE0E00A 2 Gb
     - Toshiba THGBM5G6A2JBAIR 8Gb
     - Qualcomm WTR1605L (LTE amp), Avago ACPM-7251 (GSM, EDGE, UMTS amp), Murata SS2908001 (WiFi, Bluetooth), Qualcomm MDM9215M (LTE, GSM, EDGE, UMTS modem), Broadcom 20793S(NFC)
     - 1.3 MP 'Y411A'
     - 8 MP 'AC2AD O5A261'
     - LG Bl-T5 @ 3.8V, 2100 mAh
     - Qualcomm WCD9310
     - Synaptics S7020A (controller)
     - LG LH467WX1
     - Avago 3012 (GNSS)
     - Invensense MPU-6050 6-Axis (Gyro + Acc),
     - SlimPort ANX7808 SlimPort Transmitter(HDMI out), Qualcomm PM8921 & PM8821 (Power Management), Avago A5702, A5704, A5505 (?)
   * - `Asus Nexus 7 (2012) <sub page>`_
     - ?
     - ?
     - ?
     - ?
     - NVIDIA T30L Tegra 3 Quadcore @ 1.2 GHz
     - 416 MHz twelve-core Nvidia GeForce ULP
     - 2 x Hynix H5TC2G83CFR 1GB DDR3 RAM
     - (8Gb version:) Kingston KE44B-26BN/8GB
     - AzureWave AW-NH665 (Wifi + Bluetooth?), Broadcom BCM4751 (GPS receiver), NXP 65N04 (NFC),
     - Camera Front
     - Camera Back
     - ASUS C11-ME370T @ 3.7V, 4325mAh
     - Realtek ALC5642
     - ELAN eKTF36248WS EKTF3624 (16-bit signal processor MCU) + ELAN eKTH10368WS EKTH1036 (controller)
     - Texas Instruments SN75LVDS83B (LVDS LCD display driver) + 7" Hydis HV070WX2 (display)
     - Navigation
     - Invensense MPU-6050 6-Axis(Gyro + Acc)
     - Max 77612A (Inverting Switching regulator?)
   * - :doc:`Asus Nexus 7 (2013) WiFi Edition <flo>`
     - flo
     - -
     - -
     - Qualcomm Snapdragon S4 Pro (APQ8064–1AA)
     - Krait 300 (ARMv7) Quadcore @ 1.5 GHz
     - Qualcomm Adreno 320
     - 4 x Elpida J4216EFBG 512 MB DDR3L SDRAM
     - SK Hynix H26M52003EQR 16 GB eMMC
     - Qualcomm Atheros WCN3660 (Wifi, Bluetooth, FM)
     - Camera Front
     - Camera Back
     - ASUS C11P1303 @ 3.8 V, 3950 mAh
     - Sound
     - ELAN eKTH325BAWS(controller?)
     - Display
     - Navigation
     - Sensors
     - Analogix ANX7808 SlimPort (HDMI transmitter), Texas Instruments BQ51013B (Inductive Charging Controller), Qualcomm PM8921 (Power Management)
   * - :doc:`Asus Nexus 7 (2013) GSM Edition <deb>`
     - deb
     - Halium 7.1 working
     - -
     - Qualcomm Snapdragon S4 Pro (APQ8064–1AA)
     - Krait 300 (ARMv7) Quadcore @ 1.5 GHz
     - Qualcomm Adreno 320
     - 4 x Elpida J4216EFBG 512 MB DDR3L SDRAM
     - SK Hynix H26M52003EQR 16 GB eMMC
     - Qualcomm Atheros WCN3660 (Wifi, Bluetooth, FM)
     - Camera Front
     - Camera Back
     - ASUS C11P1303 @ 3.8 V, 3950 mAh
     - Sound
     - ELAN eKTH325BAWS(controller?)
     - Display
     - Navigation
     - Sensors
     - Analogix ANX7808 SlimPort (HDMI transmitter), Texas Instruments BQ51013B (Inductive Charging Controller), Qualcomm PM8921 (Power Management)
   * - :doc:`BQ Aquaris E4.5 <krillin>`
     - krillin
     - no work so far
     - -
     - Mediatek MT6582V (1447-XAZAHH AEL32076)
     - ARMv7 Quadcore @ 1.3 GHz
     - ARM Mali-400MP2
     - SKhynix H9TP65A8JDAC PRKGM 510A (2MYRV05bQ3) 1GB
     - Storage
     - MTK MT6166V 1429AMJR BTP12059 (RF Receiver), Skyworks 77768-1 41741.1 1502 MX (WCDMA, HSDPA, HSPA+, HSUPA,LTE power amp - band VIII), Skyworks Inc. 77761-2 88219.1 1451 MX (WCDMA, HSDPA, HSPA+, HSUPA,LTE power amp - band VIII)
     - Q Tech F5648AV
     - C150201
     - bq GB/T18287-2013 @ 3.8V, 2150 mAh
     - Sound
     - Touch screen
     - Display
     - Skyworks Inc. 77584-11 4459C2 1445CN (GSM, GPRS)
     - Sensors
     - Mediatek MT6323GA 1444-AGTH CTGRS355 (Power Management, 435 HWW DM (?), 8736 ABI3 (?), sAY 2W (?), KAY 0C(?), T260 EoE5 (?), 0000 4C28 6071(?), 0000 5102 6154(?)
   * - Shift 5.1
     - Codename
     - no work done yet
     - -
     - Mediatek MT6582V (1541-XAHHAH CTTCV844)
     - ARMv7 Quadcore @ 1.3 GHz
     - ARM Mali-400MP2
     - Samsung KMR820001M-B609 2GB LPDDR2
     - Storage
     - Mediatek MT6627 Diplexer QVL (WIFI/BT/GPS), Mediatek MT6166V (RF transceiver)
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - GOODiX GT9147 (controller)
     - Display
     - AIROHA AP6684 (GPRS)
     - Sensors
     - Mediatek MT6323GA (Power Management)
   * - Wiko Pulp 4G
     - Codename
     - no work so far
     - -
     - Qualcomm Snapdragon 410 (MSM8916)
     - CPU
     - GPU
     - SK hynix H9TQ17ABJTMC 2GB eMMC
     - Storage
     - Skyworks 77648-11 (multiband Power amp, Qualcomm WTR4905 (RF transceiver), Qualcomm WCN3620 (WiFi)
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Qualcomm PM8916 (Power management), SGM3140B (LED driver)
   * - :doc:`Asus Zenfone 5 <T00F>`
     - T00F
     - work in progress
     - Kernel
     - SoC
     - CPU
     - GPU
     - RAM
     - Storage
     - Connectivity
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Other
   * - :doc:`Asus Zenfone 2 Laser <Z00L>`
     - Z00L
     - Halium 7.1 working
     - v3.10.108
     - Qualcomm MSM8939 (Snapdragon 615) / Qualcomm MSM8916 (Snapdragon 410)
     - 8/4x Cortex A53 (1.7/1.0 GHz/1.2 GHz)
     - Adreno 405/306
     - 2 GB
     - 16 GB + up to 128 GB
     - 2G bands: 850 900 1800 1900 MHz GSM | 3G bands: 850 900 1700 1900 2100 MHz HSDPA | 4G bands: 2100 1900 1800 1700(AWS) 850 2600 900 700 800 MHz
     - 5 MP (No flash)
     - 13 MP (LED flash)
     - 3000 mAh
     - MSM89**sndcardm
     - ft5*46
     - IPS LCD capacitive touchscreen, 16M colors
     - GPS
     - Accelerometer | Gyroscope | Proximity sensor | Compass
     - Other
   * - :doc:`BQ Aquaris U <chaozu>`
     - chaozu
     - Halium porting started
     - 3.18.31 based
     - SoC
     - CPU
     - GPU
     - RAM
     - Storage
     - Connectivity
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Other
   * - :doc:`Moto G 2014 <titan>`
     - titan
     - Halium 7.1 working
     - Kernel
     - SoC
     - CPU
     - GPU
     - RAM
     - Storage
     - Connectivity
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Other
   * - :doc:`Sony Xperia Z <yuga>`
     - yuga
     - Halium 7.1 working
     - Kernel
     - SoC
     - CPU
     - GPU
     - RAM
     - Storage
     - Connectivity
     - Camera Front
     - Camera Back
     - Battery
     - Sound
     - Touch screen
     - Display
     - Navigation
     - Sensors
     - Other
   * - :doc:`Sony Xperia L <taoshan>`
     - taoshan
     - Halium 7.1 can be installed, but does not work, yet
     - v3.4.0
     - Qualcomm MSM8230 Snapdragon 400
     - Dual-core 1.0 GHz Krait
     - Adreno 305
     - 1GB
     - 8GB
     - Connectivity?
     - VGA
     - 8 MP
     - Li-Ion 1750 mAh
     - Sound?
     - TFT capacitive touchscreen
     - Display?
     - A-GPS
     - Accelerometer, proximity, compass
     - Other?
   * - :doc:`HTC 10 <pme>`
     - pme
     - Halium 7.1 working
     - v3.18.31
     - Snapdragon 820 (MSM8996)
     - Quad-core ARMv8-A (2x2.15 GHz Kryo & 2x1.6 GHz Kryo)
     - Adreno 530
     - 4 GB LPDDR4 RAM **??**
     - 32 or 64 GB **??** + microSD up to 256 GB
     - Broadcom BCM4359 (Wi-Fi), NFC, BT 4.2, Display Port, Chromecast, DLNA™, AirPlay™, Miracast™ **??**
     - Samsung S5K4E6
     - Sony Exmor R IMX377
     - Non-removable Li-Ion 3.8 V, 11.5 Wh (3,000 mAh) **??**
     - Sound **??**
     - Touch screen **??**
     - Super LCD 5 (2560 x 1440 pixels) **??**
     - GPS + GLONASS + (Beidou) Navigation **??**
     - Ambient light sensor, Proximity sensor, Motion G-sensor, Compass sensor, Gyro sensor, Magnetic sensor, Fingerprint sensor, Sensor Hub - **??**
     - Other **??**
   * - :doc:`Xiaomi Redmi2/Prime <wt88047>`
     - wt88047
     - Halium 7.1 working
     - 3.10.49
     - Snapdragon 410 (MSM8916)
     - Quad-Core ARMv8 (4x1.3Ghz)
     - Adreno 306
     - 1GB/2GB LPDDR3
     - 8GB/16GB + MicroSd upto 64GB
     - WiFi, Bluetooth4.1, DLNA
     - 2 MP
     - 8 MP
     - 2,400 mAh [removable]
     - Sound **??**
     - Touch screen **?**
     - IPS LCD (1280 x 720 pixels)
     - GPS + GLONASS
     - Ambient light sensor, Proximity sensor, Motion G-sensor, Compass sensor, Gyro sensor, Magnetic sensor
     - Other **?**
   * - :doc:`OnePlus 3(T) <oneplus3>`
     - oneplus3
     - Halium 7.1 working
     - v3.18.31
     - **3:** Snapdragon 820 (MSM8996) / **3T:** Snapdragon 821 (MSM8996Pro)
     - Quad-core Kryo **3:** 2 x 2.15 GHz + 2 x 1.6 GHz / **3T:** 2 x 2.35 GHz + 2 x 1.6 GHz
     - Adreno 530
     - 6 GB LPDDR4
     - **3:** 64 GB UFS 2.0 / **3T:** 64/128 GB UFS 2.0
     - Wi-Fi, Bluetooth 4.2, DLNA
     - **3:** Sony IMX179 Exmor R (8MP) / **3T:** Samsung (16MP)
     - Sony IMX298 Exmor RS (16MP)
     - **3:** Non-removable Li-Ion 3000 mAh / **3T:** Non-removable Li-Ion 3400 mAh
     - Sound **?**
     - Touch screen **?**
     - Optic AMOLED (1080x1920)
     - GPS, A-GPS, GLONASS, BeiDou
     - Proximity, Light, Accelerometer, Compass, Gyroscope, Fingerprint, Hall
     - Other **?**
   * - :doc:`Motorola Moto G5 <cedric>`
     - cedric
     - No progress yet
     - Kernel **?**
     - Qualcomm MSM8937 Snapdragon 430
     - Octa-core Cortex-A53 (4 × 1.4 GHz + 4 × 1.1 GHz)
     - Adreno 505
     - **XT1676:** 3 GB / **???:** 2 GB
     - **XT1676:** 16 GB / **???:** 32GB
     - Wi-Fi, Bluetooth 4.2
     - OV5695, 5MP, no flash
     - IMX258, 13MP, LED flash, phase detection autofocus
     - Removable Li-Ion 2800 mAh
     - Speaker, Microphone, 3.5mm Headphone Jack **?**
     - Capacitive Touch screen **?**
     - IPS LCD (1080x1920)
     - GPS, A-GPS, GLONASS
     - Ambient Light Sensor, Fingerprint, Accelerometer, Proximity, Gyroscope
     - Other **?**
      
Sources
^^^^^^^

Since there are no sub pages yet, gathering links for the examples here:

OnePlus 5
~~~~~~~~~~


* `Oneplus 5 iFixit teardown <https://www.ifixit.com/Teardown/OnePlus+5+Teardown/94173>`_
* `Oneplus 5 Wikipedia <https://en.wikipedia.org/wiki/OnePlus_5>`_

Samsung Galaxy S8+
~~~~~~~~~~~~~~~~~~


* `Samsung Galaxy S8+ iFixit teardown <https://www.ifixit.com/Teardown/Samsung+Galaxy+S8%2B+Teardown/87086>`_
* `Samsung Galaxy S8+ GSMArena <https://www.gsmarena.com/samsung_galaxy_s8+-8523.php>`_
* `Samsung Galaxy S8+ DeviceSpecifications <https://www.devicespecifications.com/en/model/2c0b4253>`_
* `Samsung Galaxy S8(+) Website <http://www.samsung.com/global/galaxy/galaxy-s8/>`_

Samsung Galaxy S8
~~~~~~~~~~~~~~~~~


* `Samsung Galaxy S8 iFixit teardown <https://www.ifixit.com/Teardown/Samsung+Galaxy+S8+Teardown/87136>`_
* `Samsung Galaxy S8 GSMArena <https://www.gsmarena.com/samsung_galaxy_s8-8161.php>`_
* `Samsung Galaxy S8 DeviceSpecifications <https://www.devicespecifications.com/en/model/402341d2>`_
* `Samsung Galaxy S8(+) Website <http://www.samsung.com/global/galaxy/galaxy-s8/>`_

Shift 5.1
~~~~~~~~~


* `Shift 5.1 iFixit teardown <https://www.ifixit.com/Teardown/Shift5.1+Teardown/62850>`_

Wiko Pupl 4G
~~~~~~~~~~~~


* `Pupl 4G iFixit teardown <https://www.ifixit.com/Teardown/Wiko+Pulp+4G+Teardown/64584>`_

Nexus 5
~~~~~~~


* `Nexus 5 iFixit teardown <https://de.ifixit.com/Teardown/Nexus+5+Teardown/19016>`_
* `Nexus 5 Wikipedia <https://en.wikipedia.org/wiki/Nexus_5>`_
* `Nexus 5 Slideshare on Snapdragon 800 <https://de.slideshare.net/jjwu6266/qualcomm-snapdragon-800-mobile-device>`_

Nexus 5X
~~~~~~~~


* `Nexus 5X iFixit teardown <https://de.ifixit.com/Teardown/Nexus+5X+Teardown/51318>`_
* `Nexus 5X Wikipedia <https://en.wikipedia.org/wiki/Nexus_5X>`_

Oneplus One
~~~~~~~~~~~


* `Oneplus One iFixit teardown <https://de.ifixit.com/Teardown/OnePlus+One+Teardown/26484>`_
* `Oneplus One Wikipedia <https://en.wikipedia.org/wiki/OnePlus_One>`_

Nexus 4
~~~~~~~


* `Nexus 4 iFixit teardown <https://www.ifixit.com/Teardown/Nexus+4+Teardown/11781>`_
* `Nexus 4 Wikipedia <https://en.wikipedia.org/wiki/Nexus_4>`_
* `Nexus 4 Kernel @ launchpad <https://launchpad.net/ubuntu/+source/linux-mako>`_

Fairphone 2
~~~~~~~~~~~


* `Fairphone 2 iFixit teardown <https://www.ifixit.com/Teardown/Fairphone+2+Teardown/52523>`_
* `Fairphone 2 UBP dev info page <https://wiki.ubports.com/wiki/Fairphone-2-Developer-Information>`_
* `Fairphone 2 Wikipedia <https://en.wikipedia.org/wiki/Fairphone_2>`_
* `Fairphone 2 Kernel Makefile @ github/UBP <https://github.com/ubports/android_kernel_fairphone_fp2/blob/fp2-sibon/Makefile>`_

Nexus 7 (2012)
~~~~~~~~~~~~~~


* `Nexus 7 2012 iFixit teardown <https://www.ifixit.com/Teardown/Nexus+7+Teardown/9623>`_
* `Nexus 7 2012 Wikipedia <https://en.wikipedia.org/wiki/Nexus_7_(2012>`_

Nexus 7 (2013) Wifi-only = flo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


* `Nexus 7 2013 iFixit teardown <https://www.ifixit.com/Teardown/Nexus+7+2nd+Generation+Teardown/16072>`_
* `Nexus 7 2013 Wikipedia <https://en.wikipedia.org/wiki/Nexus_7_(2013>`_

BQ Aquaris E4.5
~~~~~~~~~~~~~~~

* `Aquaris E4.5 Wikipedia <https://en.wikipedia.org/wiki/BQ_Aquaris_E4.5>`_

HTC 10
~~~~~~


* `HTC 10 Wikipedia <https://en.wikipedia.org/wiki/HTC_10>`_
* `HTC 10 GSMArena <https://www.gsmarena.com/htc_10-7884.php>`_
* `HTC 10 DeviceSpecifications <https://www.devicespecifications.com/en/model/97ba3b52>`_
* `HTC 10 iFixit <https://www.ifixit.com/Device/HTC_10>`_
* `HTC 10 LOS <https://github.com/LineageOS/lineage_wiki/blob/master/_data/devices/pme.yml>`_
* `HTC 10 Website <https://www.htc.com/us/smartphones/htc-10>`_

Asus Zenfone 2 Laser (Z00L)
~~~~~~~~~~~~~~~~~~~~~~~~~~~


* `Asus Zenfone 2 Laser Z00L LOS <https://wiki.lineageos.org/devices/Z00L>`_

Xiaomi Redmi2/Prime (wt88047)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* `Xiaomi Redmi 2/Prime GSM-Arena <https://www.gsmarena.com/xiaomi_redmi_2-6884.php>`__
* `Xiaomi Redmi 2/Prime Fonearena <http://www.fonearena.com/xiaomi-redmi-2_6117.html>`__
* `Wingtech Wt88047 LOS <https://wiki.lineageos.org/devices/wt88047>`__

OnePlus 5
~~~~~~~~~~

* `OnePlus 3 Wikipedia <https://en.wikipedia.org/wiki/OnePlus_3>`_
* `OnePlus 3T Wikipedia <https://en.wikipedia.org/wiki/OnePlus_3T>`_
* `OnePlus 3 GSMArena <https://www.gsmarena.com/oneplus_3-7995.php>`_
* `OnePlus 3T GSMArena <https://www.gsmarena.com/oneplus_3t-8416.php>`_
* `OnePlus 3 DeviceSpecifications <https://www.devicespecifications.com/en/model/437a3c9b>`_
* `OnePlus 3T DeviceSpecifications <https://www.devicespecifications.com/en/model/446c3f91>`_
* `OnePlus 3 iFixit teardown <https://www.ifixit.com/Teardown/Oneplus+3+Teardown/74012>`_
* `OnePlus 3(T) LOS <https://github.com/LineageOS/lineage_wiki/blob/master/_data/devices/oneplus3.yml>`_
* `OnePlus 3 Website <https://oneplus.net/3>`_
* `OnePlus 3T Website <https://oneplus.net/3t>`_
