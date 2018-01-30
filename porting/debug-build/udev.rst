Add udev rules
==============

Now that you're logged in, you must create some udev rules to allow some tests to access your hardware. Run the following command, replacing [codename] with your device's codename.::

    cat /var/lib/lxc/android/rootfs/ueventd*.rc|grep ^/dev|sed -e 's/^\/dev\///'|awk '{printf "ACTION==\"add\", KERNEL==\"%s\", OWNER=\"%s\", GROUP=\"%s\", MODE=\"%s\"\n",$1,$3,$4,$2}' | sed -e 's/\r//' >/etc/udev/rules.d/70-[codename].rules

Now, reboot the device.

.. todo::

    Update these instructions to update udev rules on "host" machine. The ueventd*rc files are already in $OUT/root/ , so it needs updating for path and then instead of writing it to /etc/udev/rules.d/70-codename.rules, writing it to local file and then adb pushing it while in recovery.

.. todo::

    Add information about adding udev rules in the lxc-android repository.
