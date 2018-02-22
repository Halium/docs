
Porting FAQ
===========

This is a list of common error messages and corresponding fixes people run into when porting new devices to Halium. 
Contributions welcome!

Getting ``kgsl kgsl-3d0: |_load_firmware| request_firmware(a330_pm4.fw) failed: -2 … kgsl kgsl-3d0: |adreno_init| Reading pm4 microcode failed a330_pm4.fw``
------------------------------------------------------------------------------------------------------------------------------------------------------------

Toggle kernel option ``CONFIG_FW_***LOADER``

Dmesg shows systemd errors when running ``switch_root /target /sbin/init``
--------------------------------------------------------------------------

.. code-block:: guess
   systemd[1]: Failed to determine whether /sys/fs/cgroup is a mount point: Too many levels of symbolic links
   systemd[1]: Failed to mount cgroup at /sys/fs/cgroup/systemd: NO such filE oR directory
   systemd[1]: Freezing execution.

There's a patch on hammerhead kernel from Linus Torvalds you need to apply: [PATCH] vfs: Fix /proc/<tid>/fdinfo/<fd> file handling
https://github.com/Halium/android_kernel_lge_hammerhead/commit/25437b2a54dd619a96e268ecaf303b089aa785e4


Compiler error for kvfree with apparmor directory
-------------------------------------------------

.. code-block:: guess
   ../../../../../../kernel/samsung/s3ve3g/security/apparmor/apparmorfs.c: In function 'aa_simple_write_to_buffer': 
   ../../../../../../kernel/samsung/s3ve3g/security/apparmor/apparmorfs.c:110:3: error: implicit declaration of function 'kvfree' [-Werror=implicit-function-declaration]
   kvfree(data);

Use this patch:
https://github.com/ubports/android_kernel_moto_shamu/commit/83f949a8de673fe45499d1741da8654831a5afae

Build errors for systemimage which is trying to build an apk
------------------------------------------------------------

Remove all apks from the makefiles in ``vendor/$vendor/$device``
Also check the vendor folders of your dependencies.

My device is constantly rebooting. How do I get a new last_kmsg?
----------------------------------------------------------------

Enable the following configs:

.. code-block:: guess
   CONFIG_ANDROID_RAM_CONSOLE=y
   CONFIG_ANDROID_RAM_CONSOLE_ENABLE_VERBOSE=y

Also be sure to not turn your device off. 
You only get a usefull last_kmsg if you reboot without losing power.

My device is constantly rebooting. I can get into telnet but it bootloops after ``echo continue > /init-ctl/stdin``
-------------------------------------------------------------------------------------------------------------------

There could be something wrong with your lxc container. Try the following to disable it for the moment:

.. code-block:: guess
   cd target/
   TERM=linux HOME=/root PATH=/sbin:/bin:/usr/sbin:/usr/bin:$PATH chroot . /bin/bash
   systemctl disable lxc@android
   systemctl mask lxc@android
   exit
   echo continue > /init-ctl/stdin

SSH into upborts rootfs fails with ``Connection reset by 10.15.19.82 port 22``
------------------------------------------------------------------------------

It's a known problem with the sshd, go into chroot and add this in /etc/init/ssh.override:

.. code-block:: guess
   start on startup
   exec /usr/sbin/sshd -D -o PasswordAuthentication=yes

Then remove the overlay: ``rm -r /data/system-data``

I can't do video tests, but vibrator, wifi and lights work
----------------------------------------------------------

Have you added the caf repo to your sources.list? If not run the following and reboot:

.. code-block:: guess
   . /etc/environment
   echo "deb http://repo.halium.org/caf xenial main" >> /etc/apt/sources.list.d/halium-caf.list
   apt -get update
   apt-get dist-upgrade

Side node: CAF means Code Aurora Forum. It's where Qualcomm releases code for their phone processors.

Getting network errors
----------------------

Use nmtui to connect to wifi.
If you can't ping any website add this to your defconfig: ``CONFIG_ANDROID_PARANOID_NETWORK=n``


During hwcomposer test I found the following errors in logcat
-------------------------------------------------------------

.. code-block:: guess
   W Adreno-GSL: <gsl_ldd_control:475>: ioctl fd 8 code 0xc0140933 (IOCTL_KGSL_TIMESTAMP_EVENT) failed: errno 22 Invalid argument
   W Adreno-GSL: <ioctl_kgsl_syncobj_create:2984>: (9, 1, 62845) fail 22 Invalid argument
   W Adreno-EGLSUB: <SwapBuffers:1339>: gsl_device_3d_add_fence_event failed
   W Adreno-EGL: <qeglDrvAPI_eglSwapBuffers:3890>: EGL_BAD_SURFACE

Have you added CAF repo and libhybris? Make sure you upgrade libhybris too.

I get make errors
-----------------
.. code-block:: guess
   find: ‘device/*/generic’: No such file or directory
   find: ‘device/unknown’: No such file or directory
   find: ‘device/android’: No such file or directory
   halium/hybris-boot/Android.mk:67: ********************* /boot appears to live on ERROR: *fstab* not found
   halium/hybris-boot/Android.mk:68: ********************* /data appears to live on ERROR: *fstab* not found
   halium/hybris-boot/Android.mk:71: *** There should be a one and only one device entry for HYBRIS_BOOT_PART and HYBRIS_DATA_PART.

Make sure you run lunch or breakfast before running make.



