
Early Init
==========

Hybris-boot offers a telnet service that you can use to debug the very early init of your port. This service will be exposed if the Halium system has failed to boot for any reason.

Determining if this is needed
-----------------------------

While bringing the USB network interface up, the boot image will write a few debug messages. These debug messages are communicated via a clever hack of resetting the serial number of the usb connection.

The steps in detail are:

* Execute this command to watch the changes in the usb serial number::

    while : ; do lsusb -v 2>/dev/null | grep -Ee 'iSerial +[0-9]+ +[^ ]' ; done | uniq
  
* Boot your newly built image
* Watch the output of the lsusb command above. It will put out lines like this::

     iSerial                 3 01234567
     iSerial                 3 Mer Debug setting up (DONE_SWITCH=no)
     iSerial                 3 Mer Debug telnet on port 23 on usb0 192.168.2.15 - also running udhcpd

If you get a line similar to the last two above, Telnet is running. Continue to the next section to debug it.

If you instead get the line ``GNU/Linux devices on rndis0 10.15.19.82``, the system has booted successfully. Move to :doc:`logging-in` to continue your debugging.

Debugging via telnet
--------------------

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

Now you have terminal access to the system running from initramfs. The first command to run once you're logged in is ``cat diagnosis.log`` to see if it has any hints.

Forcing debug mode
------------------

If the device simply reboots when trying to boot and does not bring up telnet, you may build and use the ``hybris-recovery.img`` file to attempt to force a shell to come up. To do this, set up your build tree and issue the following command::

    mka hybris-recovery

The file will be in the standard $OUTDIR. Simply flash it in the same way you did for ``hybris-boot.img``.

Common errors
-------------

The device reboots after leaving hybris-recovery
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If your device reboots after you leave hybris-recovery by running ``echo continue > /init-ctl/stdin``,there could be something wrong with your lxc container. Try the following in the hybris-recovery shell to disable it for the moment::

   TERM=linux HOME=/root PATH=/sbin:/bin:/usr/sbin:/usr/bin:$PATH chroot target/ /bin/bash
   systemctl disable lxc@android
   systemctl mask lxc@android
   exit
   echo continue > /init-ctl/stdin

You should then be offered SSH. See :doc:`logging-in` for more details. Once you are logged in, you can try to troubleshoot what is causing your reboots by running ``systemctl unmask lxc@android && systemctl start lxc@android``.

Bootloop: "Too many levels of symbolic links" when leaving hybris-boot
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: guess

   systemd[1]: Failed to determine whether /sys/fs/cgroup is a mount point: Too many levels of symbolic links
   systemd[1]: Failed to mount cgroup at /sys/fs/cgroup/systemd: NO such filE oR directory
   systemd[1]: Freezing execution.

There's a patch on hammerhead kernel from Linus Torvalds you need to apply: `Fix /proc/<tid>/fdinfo/<fd> file handling`_.

The device reboots with hybris-recovery
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are several cases in which telnet will not be exposed, such as when the device fails to load the kernel or initramfs, or when an in-kernel driver decides to cause a kernel panic very early. In this case, the phone will almost immediately reboot when it starts, even when using ``hybris-recovery``. You may be able to :doc:`read the previous boot's kernel message buffer <dmesg>`. Please have that ready and :ref:`contact us for help <support-channels>`.

None of these describe my issue
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You may be able to :doc:`read the previous boot's kernel message buffer <dmesg>`. Please have that ready and :ref:`contact us for help <support-channels>`.


.. _Fix /proc/<tid>/fdinfo/<fd> file handling: https://github.com/Halium/android_kernel_lge_hammerhead/commit/25437b2a54dd619a96e268ecaf303b089aa785e4