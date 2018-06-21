
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

You may now reboot using '/sbin/reboot' your device into Halium.

Once your device is booted, you should see that you have a new network interface again. Look at the output of ``ip link show``, the name will be e.g. enp0s29u1u1. rndis0 is not working on most kernels. Assign it a fake MAC address (if the default one is all 00s) and an IP of 10.15.19.100::

    ip link set <devicename> address 02:11:22:33:44:55
    ip address add 10.15.19.100 dev <devicename>
    ip link set <devicename> up

 Once finished, you should be able to do the following to log in::

    ssh root@10.15.19.82
