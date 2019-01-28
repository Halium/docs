Common kernel build errors
==========================

These are the ``hybris-boot`` build errors most commonly seen in the Halium community. If you have found and fixed a new error, please document the steps that you have taken to fix it.

Implicit declaration of 'kvfree'
--------------------------------

If you receive something similar to the following error::

   ../../../../../../kernel/[...]/[...]/security/apparmor/apparmorfs.c: In function 'aa_simple_write_to_buffer':
   ../../../../../../kernel/[...]/[...]/security/apparmor/apparmorfs.c:110:3: error: implicit declaration of function 'kvfree' [-Werror=implicit-function-declaration]
   kvfree(data);

Apply the patch `nick kvfree() from apparmor`_.


.. _nick kvfree() from apparmor: https://github.com/ubports/android_kernel_moto_shamu/commit/83f949a8de673fe45499d1741da8654831a5afae


'kuid_t' (sdcardfs, cgroup) error
---------------------------------

Example of the error::

   ../../../../../../kernel/lenovo/msm8916/kernel/cgroup.c:2138:37: error: invalid operands to binary != (have 'kuid_t' and 'kuid_t')
   if (current != task && cred->euid != tcred->uid &&

   ../../../../../../kernel/lenovo/msm8916/kernel/cgroup.c:2139:18: error: invalid operands to binary != (have 'kuid_t' and 'kuid_t')
       cred->euid != tcred->suid)

Set ``CONFIG_USER_NS`` to ``n`` in your defconfig.

Firmware class error
--------------------

Example of the error::

   ../../../../../../kernel/lenovo/msm8916/drivers/base/firmware_class.c: In function '_request_firmware':
   ../../../../../../kernel/lenovo/msm8916/drivers/base/firmware_class.c:1226:38: warning: passing argument 2 of 'fw_load_from_user_helper' from incompatible pointer type
   error, forbidden warning: firmware_class.c:1226

Set ``CONFIG_FW_LOADER_USER_HELPER`` to ``y`` in your defconfig.

ECRYPTFS error
--------------

Example of the error::

   ../../../../../../kernel/lenovo/msm8916/fs/ecryptfs/file.c: In function 'ecryptfs_readdir':
   ../../../../../../kernel/lenovo/msm8916/fs/ecryptfs/file.c:130:16: error: assignment of read-only member 'actor'
  buf.ctx.actor = ecryptfs_filldir;

Apply `this patch from bullhead`_.

.. _this patch from bullhead: https://github.com/usb-bullhead-ubuntu-touch/kernel_msm/commit/b0403f0ee02e6582017cdb45b4c0c72b00cc72eb
