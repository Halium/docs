
USB Network tethering
=====================

It is possible to connect the device to the internet via usb network tethering. This can be helpful when you haven't gotten Wi-Fi working (yet).

The instructions below assume you're running Ubuntu >=16.04. Earlier versions of Ubuntu or other distributions will probably work similarly if ``iptables`` is installed.

You need three things:

  * The name of your computers network device which connects to the internet. You can check ``ip link`` to determine this. Likely it is something like ``wlan0`` or ``eth0``. We'll call this ``[INTERNET]``.
  * The name of your computers usb network device which connects to the "rndis" network. This is the same as described for the :ref:`telnet debugging access <telnet>`. We'll call this ``[USBNETWORK]``.
  * Lastly, you need your computers IP address on this network. If you are connecting with :ref:`telnet <telnet>` then this is ``192.168.2.1``. If you are connecting with :ref:`ssh <ssh>` then this is ``10.15.19.100``.

With this information you run the following commands::

   sudo sysctl net.ipv4.ip_forward=1
   sudo iptables -t nat -A POSTROUTING -o [INTERNET] -j MASQUERADE
   sudo iptables -A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
   sudo iptables -A FORWARD -i [USBNETWORK] -o [INTERNET] -j ACCEPT

Now, run the following command as root on your device:

If you're in initrd debug (telnet)::

   route add default gw 192.168.2.1

If you're in the real rootfs (ssh)::

   ip route add default via 10.15.19.100

Then try ``ping 8.8.8.8`` from the phone. The pings should go through.

To add a DNS server on your device, edit ``/etc/resolv.conf`` and add the line ``nameserver 8.8.8.8``. This is NOT the recommended way to add a nameserver on Debian, but it works reliably when you can't depend on other options. Your changes will be overwritten on reboot, so you will need to perform them again.


You should now be able to ``ping debian.org`` and generally have internet access on the device.
