
USB Network tethering
=====================

It is possible to connect the device to the internet via usb network tethering. This can be helpful when you haven't gotten Wi-Fi working (yet).

The instructions below assume you're running Ubuntu >=16.04. Earlier versions of Ubuntu or other distributions will probably work similarly if ``iptables`` is installed.

You need three things:
  * The name of your computers network device which connects to the internet. You can check ``ip link`` to determine this. Likely it is something like ``wlan0`` or ``eth0``. We'll call this ``[INTERNET]``.
  * The name of your computers usb network device which connects to the "rndis" network. This is the same as described for the telnet debugging access. As with the instructions there, we call this ``[USBNETWORK]``. 
  * Lastly, you need your computers IP address on this network. Following the telnet instructions this is ``192.168.2.1``.

You'll need them for the following commands::

   sudo sysctl net.ipv4.ip_forward=1
   sudo iptables -t nat -A POSTROUTING -o [INTERNET] -j MASQUERADE
   sudo iptables -A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
   sudo iptables -A FORWARD -i [USBNETWORK] -o [INTERNET] -j ACCEPT

Then, run the following command using your telnet connection on your phone::

   route add default gw 192.168.2.1

Then try ``ping 8.8.8.8`` from the phone. The pings should go through.

To temporarily add a DNS server on your phone, edit ``/etc/resolv.conf`` and add the line ``nameserver 8.8.8.8``. This is NOT the recommended way to add a nameserver on Debian, but it works reliably when you can't depend on other options. Your changes will be overwritten on reboot, so you will need to perform them again.


You should now be able to ``ping debian.org`` and generally have internet access on the device.
