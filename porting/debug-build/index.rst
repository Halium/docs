
Debug Halium
============

Reading kernel logs
-------------------

To find out what happened during an unsuccessful boot you can check the kernel log files. These can usually be retrieved from ``/proc/last_kmsg`` after rebooting the device into another, working system. A precondition for this is that you have a system that you can successfully boot, such as TWRP.


#. Boot your newly built image
#. Wait for it to fail
#. Reboot the device into the working system.
#. Retrieve the kernel log with ``adb shell cat /proc/last_kmsg > ~/last_kmsg``
#. Read ``~/last_kmsg`` and find out what went wrong

Debugging via telnet
--------------------

The hybris-boot image can offer you a telnet interface to access the system on the device even if it does not come up fully. To this end, the usb function of the device will be reconfigured to work as a network interface. While bringing this network interface up, the boot image will write a few debug messages. These debug messages are communicated via a clever hack of resetting the serial number of the usb connection. Once you see that the usb networking and telnet have been set up, you can configure the usb networking on your desktop and then telnet into the system.

The steps in detail are:

* Execute this command to watch the changes in the usb serial number::

    while : ; do lsusb -v 2>/dev/null | grep -Ee 'iSerial +[0-9]+ +[^ ]' ; done | uniq
  
* Boot your newly built image
* Watch the output of the lsusb command above. It will put out lines like this::

     iSerial                 3 01234567
     iSerial                 3 Mer Debug setting up (DONE_SWITCH=no)
     iSerial                 3 Mer Debug telnet on port 23 on usb0 192.168.2.15 - also running udhcpd

* Determine the name of the usb network device on your desktop:
    ``dmesg | tail``. You're looking for a line similar to this::

       [ 1234.123456] rndis_host 1-7:1.0 enp0s20f0u7: renamed from usb0

* In this example shown above, ``enp0s20f0u7`` is the usb network device name. Use this for the USBNETWORK below
* Check if the usb network device has a MAC address assigned::

     $ ip address show dev USBNETWORK
     6: USBNETWORK: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
      link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff

  If it shows the link/ether address ``00:00:00:00:00:00`` as shown above, you will have to manually assign the MAC address::

     ip link set USBNETWORK address 02:01:02:03:04:08

  You can set any MAC address you want, it just needs to be a valid MAC address.
* Configure usb networking::

     sudo ip address add 192.168.2.1 dev USBNETWORK
     ip address show dev USBNETWORK
     sudo ip route  add 192.168.2.15 dev USBNETWORK
     ping -c 2 192.168.2.15

* Connect with telnet: ``telnet 192.168.2.15``

Now you have terminal access to the system running from initrd.

The ``hybris-boot.img`` brings up the telnet interface if it detects a problem. Alternatively, you can use the ``hybris-recovery.img`` image which will always start telnet.

Specific hardware enablement
----------------------------

These pages will help you debug your Halium build after you've installed it.

.. toctree::
   :maxdepth: 1
   
   debug-android-userspace
   graphics
   lights
   vibrator
   wifi


References
----------

The hybris-boot image is based on work from the Sailfish OS and the `Sailfish Hardware Adaptation Development Kit porting guide <https://sailfishos.org/develop/hadk/>`_ contains valuable tips.
