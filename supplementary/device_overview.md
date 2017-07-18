# Halium Device Overview

Below are devices that
  * ( A ) **have a running Halium Image**
  * ( B ) **had a Halium image in the past**
  * ( C ) **users want to see ported**

All of these should only be document in the exact same way here and **only an overview shall be given on this page** everything that goes into more detail should please be posted on a device specific sub page!

## How to document

### Purpose
This table is meant for 2 purposes:
  * (A) give porters a **quick status reference** what has already been done in regard of Halium to a specific device or what the starting conditions are
  * (B) make hardware visible for **kernel team** to see  there may be a possibility of **a common drivers base** for multiple devices

### Table Format

Please use the following where the formatting is not obvious:

  1. First Row 'Device' is Manufacturer + Device Name and **links to the devices sub page**
  2. Second Row 'Codename' is the official Codename as stated inside the Android/Ubuntu Touch/Lineage sources
  3. Third Row  'Halium status' is a very short description like 'working fully' or 'boot loop' with the base version attached so e.g. with halium 5.1 base: 'working fully - 5.1'
  4. All following Hardware Rows **should link to a detail page about every chip**
  5. If you **only have the labels from chips available** just set them inside 'label' perhaps someone else knows more details (most common for cameras, see Nexus 4 example below)
  6. **Kernel Version Please fill this one only when there is an existing Halium image!**

### Getting the Info

  * Search **Wikipedia** for your device, a good starting points are the articles that compare [smart phones](https://en.wikipedia.org/wiki/Comparison_of_smart phones) or [tablets](https://en.wikipedia.org/wiki/Comparison_of_tablet_computers)
  * Search the [xda-developers forum](https://forum.xda-developers.com)
  * Connect to your device via adb (assuming you have some kind of Android on your phone/tablet) and search for infos using getprop or similar
  * Search for **teardowns** and scan the images for readable chips and try to find out what each one does (you may of course do a teardown on your own) good starting points for this are iFixit or Youtube Videos that show how to repair/tear down a device
  * Please **write down your sources somewhere and link to them in the device's sub page**


## Devices


|Device|Codename|Halium status|Kernel|SoC|CPU|GPU|RAM|Storage|Connectivity|Camera Front|Camera Back|Battery|Sound|Touch screen|Display|Navigation|Sensors|Other|
|:-----|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| [LG Nexus 5](devices/hammerhead.md)|hammerhead|? reference|?|Qualcomm Snapdragon 800|Krait 400 @ 4 x 2.5 GHz|Qualcomm Adreno 330|SK Hynix H9CKNNNBPTMRLR-NTM 2 GB LPDDR3-1600 RAM|Sandisk SDIN8DE4 16 GB NAND flash (15 GB version)|Qualcomm WTR1605L (LTE/HSPA+/CDMA2K/TDSCDMA/EDGE/GPS transceiver), Broadcom BCM4339 (5G & WiFi), Avago ACPM-7600 (RF power amp), Qualcomm QFE1100 (RF enevlope tracking amp)|Cam Front|Cam back|LG BL-T9 @ 3.8V, 2300 mAh|Qualcomm WCD9320|Touch Screen +  Synaptics S3350B (Controller)| Display|Navigation|InvenSense MPU-6515 (6-Axis Gyro + Acc), Asahi Kasei AK8963 (3-Axis compass), InvenSense IDG-2020 (2-Axis Gyro - for OIS)|Avago RFI335 (optocopler ?), Qualcomm PM8841 & PM8941 (power management), Analogix ANX7808 (Slimport transmitter), Texas Instruments BQ24192 (I2C controlled USB charger)|
|[Nexus 5X](devices/bullhead.md)|bullhead|? reference|?|Qualcomm Snapdragon 808|CPU|Qualcomm Adreno 418|Samsung K3QF3F30BM-QGCF 2 GB LPDDR3 RAM|Toshiba THGBMFG7C2LBAIL 16 GB eMMC|Qualcomm WTR3925 (LTE Transceiver), Skyworks 77814-11(LTE power amp), Avago ACPM7800 (GSM/Edge power amp), Qualcomm QCA6174 (WiFi), NXP PN548 (NFC), RF Micro Devices RF1149A (RF), Qualcomm QFE1100 (RF enevlope tracking) |Cam front|Sony IMX377 12.3 MP (sensor)|LG BL-T19 @ 3.8V, 2700 mAh|Qualcomm WCD9330|Touch|Display|Nav|Sens|Qualcomm SMB1358(Quick Charge), Qualcomm PMI8994 (Power management), ST Microelectronics STM32F411CE (32-bit 100 MHz ARM Cortex-M4 RISC microcontroller), Avago BFI523(?)|
|[Oneplus One](devices/bacon.md)|bacon|? reference|?|Qualcomm Snapdragon 801 MSM8974PRO-AC r2p1|Krait 400 @ 4 x 2.5 GHz|Qualcomm Adreno 330|Samsung K3QF7F70DM-QGCF 3 GB LPDDR3|Toshiba THGBMBG9D8KBAIG eMMC 5.0 64 GB|Skyworks SKY85709 (WiFi), Qualcomm WCN3680 (WiFi, Bluetooth, FM), Qualcomm WTR1625L (RF transceiver)|P5V35A Sunny Optical Technology|P13N05A Sunny Optical Technology with Sony Exmor IMX 214(sensor)|Oneplus BLP571 @ 3.8V, 3100 mAh|Qualcomm WCD9320|Synaptics S3508A(controller)|display|navi|AGD2 2402 WX9DR(gyro?)|Qualcomm PM8941 + PM8841(power management), Skyworks SKY77629-21(power amp)|
|[Fairphone 2](devices/fp2.md)|fp2|-|-|Qualcomm MSM8974AB-AB Snapdragon 801|Krait 400 (?) @ 4 x 2.5 GHz|Qualcomm Adreno 330|Samsung K3QF2F20EM 2 GB LPDDR3 RAM|Samsung KLMBG4WEBC 32 GB eMMC NAND|Qualcomm WCN3680B (WiFi + Bluetooth), Qualcomm WTR1625L (RF Receiver), RF Micro Device RF7389EU (RF amp)|Camera Front|Camera Back|? @ 3.8 V, 2420 mAh|Qualcomm WCD9320|Touch screen|Display|Navigation|ST Microelectronics LSM330DLC 6-Axis (Gyro + Acc)|Qualcomm QFE1100 (Power Management), Qualcomm PM8841 (Power Management IC)|
|[LG Nexus 4](devices/mako.md)|mako|-|-|Qualcomm Snapdragon S4 Pro (APQ8064)|Krait 300 (ARMv7) Quad core @ 1.5 GHz|Qualcomm Adreno 320|Samsung K3PE0E00A 2 Gb|Toshiba THGBM5G6A2JBAIR 8Gb|Qualcomm WTR1605L (LTE amp), Avago ACPM-7251 (GSM, EDGE, UMTS amp), Murata SS2908001 (WiFi, Bluetooth), Qualcomm MDM9215M (LTE, GSM, EDGE, UMTS modem), Broadcom 20793S(NFC)|1.3 MP 'Y411A'|8 MP 'AC2AD O5A261'|LG Bl-T5 @ 3.8V, 2100 mAh|Qualcomm WCD9310|Synaptics S7020A (controller)|LG LH467WX1|Avago 3012 (GNSS)|Invensense MPU-6050 6-Axis (Gyro + Acc), |SlimPort ANX7808 SlimPort Transmitter(HDMI out), Qualcomm PM8921 & PM8821 (Power Management), Avago A5702, A5704, A5505 (?)| 
|[Asus Nexus 7 (2012)](sub page)|?|?|?|?|NVIDIA T30L Tegra 3 Quadcore @ 1.2 GHz|416 MHz twelve-core Nvidia GeForce ULP|2 x Hynix H5TC2G83CFR 1GB DDR3 RAM|(8Gb version:) Kingston KE44B-26BN/8GB|AzureWave AW-NH665 (Wifi + Bluetooth?), Broadcom BCM4751 (GPS receiver), NXP 65N04 (NFC), |Camera Front|Camera Back|ASUS C11-ME370T @ 3.7V, 4325mAh|Realtek ALC5642|ELAN eKTF36248WS EKTF3624 (16-bit signal processor MCU) + ELAN eKTH10368WS EKTH1036 (controller)|Texas Instruments SN75LVDS83B (LVDS LCD display driver) + 7" Hydis HV070WX2 (display)|Navigation|Invensense MPU-6050 6-Axis(Gyro + Acc)|Max 77612A (Inverting Switching regulator?)|
|[Asus Nexus 7 (2013) WiFi Edition](devices/flo.md)|flo|-|-|Qualcomm Snapdragon S4 Pro (APQ8064–1AA)|Krait 300 (ARMv7) Quadcore @ 1.5 GHz|Qualcomm Adreno 320|4 x Elpida J4216EFBG 512 MB DDR3L SDRAM|SK Hynix H26M52003EQR 16 GB eMMC|Qualcomm Atheros WCN3660 (Wifi, Bluetooth, FM)|Camera Front|Camera Back|ASUS C11P1303 @ 3.8 V, 3950 mAh|Sound|ELAN eKTH325BAWS(controller?)|Display|Navigation|Sensors|Analogix ANX7808 SlimPort (HDMI transmitter), Texas Instruments BQ51013B (Inductive Charging Controller), Qualcomm PM8921 (Power Management)|


### Temp. Sources

Since there are no sub pages yet, gathering links for the examples here:

#### Nexus 5
  * [iFixit teardown](https://de.ifixit.com/Teardown/Nexus+5+Teardown/19016)
  * [Wikipedia](https://en.wikipedia.org/wiki/Nexus_5)
  * [Slideshare on Snapdragon 800](https://de.slideshare.net/jjwu6266/qualcomm-snapdragon-800-mobile-device)


#### Nexus 5X
  * [iFixit teardown](https://de.ifixit.com/Teardown/Nexus+5X+Teardown/51318)
  * [Wikipedia](https://en.wikipedia.org/wiki/Nexus_5X)


#### Oneplus One
  * [iFixit teardown](https://de.ifixit.com/Teardown/OnePlus+One+Teardown/26484)
  * [Wikipedia](https://en.wikipedia.org/wiki/OnePlus_One)


#### Nexus 4
  * [iFixit teardown](https://www.ifixit.com/Teardown/Nexus+4+Teardown/11781)
  * [Wikipedia](https://en.wikipedia.org/wiki/Nexus_4)
  * [Kernel @ launchpad](https://launchpad.net/ubuntu/+source/linux-mako)

  
#### Fairphone 2
  * [iFixit teardown](https://www.ifixit.com/Teardown/Fairphone+2+Teardown/52523)
  * [UBP dev info page](https://wiki.ubports.com/wiki/Fairphone-2-Developer-Information)
  * [Wikipedia](https://en.wikipedia.org/wiki/Fairphone_2)
  * [Kernel Makefile @ github/UBP](https://github.com/ubports/android_kernel_fairphone_fp2/blob/fp2-sibon/Makefile)

#### Nexus 7 (2012)
  * [iFixit teardown](https://www.ifixit.com/Teardown/Nexus+7+Teardown/9623)
  * [Wikipedia](https://en.wikipedia.org/wiki/Nexus_7_(2012))

#### Nexus 7 (2013) Wifi-only = flo
  * [iFixit teardown](https://www.ifixit.com/Teardown/Nexus+7+2nd+Generation+Teardown/16072)
  * [Wikipedia](https://en.wikipedia.org/wiki/Nexus_7_(2013))

