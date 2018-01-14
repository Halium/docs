
Logging in
==========

Once booted, the reference rootfs will offer an SSH connection that you can use to run tests or otherwise debug the system. Before you're able to sign in, though, you will need to change the root user's password.

To change the root user's password, reboot into TWRP and get access via ``adb shell``. Then, perform the following commands::

    mkdir /a
    mount /data/rootfs.img /a
    chroot /a /bin/bash
    . /etc/environment
    passwd

You will be prompted to change the password. Once finished, clean up::

    exit
    umount /a
    rmdir /a
    sync

You may now reboot your device into Halium.

Once your device is booted, you should see that you have a new network interface again, similar as before with telnet. Assign it an IP of 10.15.19.100::

    ip link set USBNETWORK address 02:01:02:03:04:08
    sudo ip address add 10.15.19.1 dev USBNETWORK 
    ip address show dev USBNETWORK
    sudo ip route add 10.15.19.82 dev USBNETWORK
    ping -c 2 10.15.19.82 

Now you should be able to log in::

    ssh root@10.15.19.82
