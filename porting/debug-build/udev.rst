Add udev rules
==============

You must create some udev rules to allow some tests to have access to your hardware. 

There are 2 different ways to do this:

On device:
----------

Log in on the device, you must create some udev rules to allow some tests to access your hardware. Run the following command, replacing [codename] with your device's codename::

    cat /var/lib/lxc/android/rootfs/ueventd*.rc | grep ^/dev | sed -e 's/^\/dev\///' | awk '{printf "ACTION==\"add\", KERNEL==\"%s\", OWNER=\"%s\", GROUP=\"%s\", MODE=\"%s\"\n",$1,$3,$4,$2}' | sed -e 's/\r//' >/etc/udev/rules.d/70-[codename].rules

Now, reboot the device.

On the host:
------------

Alternatively, if you want to create the file with the udev rules on your "host" machine you can run the following command inside your halium folder, replacing [codename] with your device's codename::

    cat out/target/product/[codename]/root/ueventd*.rc | grep ^/dev | sed -e 's/^\/dev\///' | awk '{printf "ACTION==\"add\", KERNEL==\"%s\", OWNER=\"%s\", GROUP=\"%s\", MODE=\"%s\"\n",$1,$3,$4,$2}' | sed -e 's/\r//' > 70-[codename].rules

You can then use either SSH or 'adb push' to push the file to the right location:

SSH:: 

    cat 70-[codename].rules | ssh 10.15.19.82 'cat > /tmp/plan.md'

ADB: Reboot into recovery to push the file to '/data/halium-rootfs/etc/udev/rules.d/' i.e.::

    adb push 70-[codename].rules /data/halium-rootfs/etc/udev/rules.d/

Send upstream:
--------------

In order for other users to be able to use the udev rules as well, it's necessary to send a pull request containing the new file to the lxc-android repository. Similar to: https://github.com/Halium/lxc-android/pull/12/files
