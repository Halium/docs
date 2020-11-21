Common kernel build errors
==========================

These are the ``hybris-boot`` build errors most commonly seen in the Halium community. If you have found and fixed a new error, please document the steps that you have taken to fix it.

Implicit declaration of 'kvfree'
--------------------------------

If you receive something similar to the following error:

.. code-block:: text

   kernel/[...]/[...]/security/apparmor/apparmorfs.c: In function 'aa_simple_write_to_buffer':
   kernel/[...]/[...]/security/apparmor/apparmorfs.c:110:3: error: implicit declaration of function 'kvfree' [-Werror=implicit-function-declaration]
   kvfree(data);

Apply the patch `nick kvfree() from apparmor`_.

'kuid_t' (sdcardfs, cgroup) error
---------------------------------

Example of the error:

.. code-block:: text

   kernel/lenovo/msm8916/kernel/cgroup.c:2138:37: error: invalid operands to binary != (have 'kuid_t' and 'kuid_t')
   if (current != task && cred->euid != tcred->uid &&

   kernel/lenovo/msm8916/kernel/cgroup.c:2139:18: error: invalid operands to binary != (have 'kuid_t' and 'kuid_t')
       cred->euid != tcred->suid)

Set ``CONFIG_USER_NS`` to ``n`` in your defconfig.

Firmware class error
--------------------

Example of the error:

.. code-block:: text

   kernel/lenovo/msm8916/drivers/base/firmware_class.c: In function '_request_firmware':
   kernel/lenovo/msm8916/drivers/base/firmware_class.c:1226:38: warning: passing argument 2 of 'fw_load_from_user_helper' from incompatible pointer type
   error, forbidden warning: firmware_class.c:1226

Set ``CONFIG_FW_LOADER_USER_HELPER`` to ``y`` in your defconfig.

ECRYPTFS error
--------------

Example of the error:

.. code-block:: text

   kernel/lenovo/msm8916/fs/ecryptfs/file.c: In function 'ecryptfs_readdir':
   kernel/lenovo/msm8916/fs/ecryptfs/file.c:130:16: error: assignment of read-only member 'actor'
   buf.ctx.actor = ecryptfs_filldir;

Apply `'patch ecryptfs to fix a build error' from bullhead`_.

'Undefined reference to pidns_operations' on Linux 3.4
------------------------------------------------------

The implementation of PID Namespacing was incomplete in the Android kernel 3.4, causing the following error:

.. code-block:: text

   fs/built-in.o:namespaces.c:ns_entries: error: undefined reference to 'pidns_operations'

To fix this issue, apply the patch `Finish implementation of PID namespace`_

'struct perf_cpu_context' has no member named 'unique_pmu'
----------------------------------------------------------

This is caused by an incomplete merge of a few changes in some 3.4 kernels:

.. code-block:: text

   kernel/fairphone/msm8974/kernel/events/core.c: In function 'perf_cgroup_switch':
   kernel/fairphone/msm8974/kernel/events/core.c:379:13: error: 'struct perf_cpu_context' has no member named 'unique_pmu'
   if (cpuctx->unique_pmu != pmu)

To fix this issue, apply `perf: Clarify perf_cpu_context::active_pmu usage by renaming it to ::unique_pmu`_

'PROC_PID_INIT_INO' undeclared here (not in a function)
-------------------------------------------------------

Somehow, the implementation of the ``/proc`` filesystem is incomplete in some 3.4 kernels:

.. code-block:: text

   kernel/fairphone/msm8974/kernel/pid.c:81:15: error: 'PROC_PID_INIT_INO' undeclared here (not in a function)
     .proc_inum = PROC_PID_INIT_INO,

Add the following line after all of the other ``#include`` lines in the file kernel/user_namespace.c similar to https://github.com/Halium/android_kernel_lge_hammerhead/commit/5754614eb43dea44a99e54898e3b83d4d96d8b83 ::

   #include <linux/proc_fs.h>

POSIX_ACL not supported in 3.18 backport
----------------------------------------

Example of the error:

.. code-block:: text

   kernel/huawei/angler/fs/ext4/inode.c: In function 'ext4_setattr':
   kernel/huawei/angler/fs/ext4/inode.c:4717:2: error: #error POSIX_ACL not supported in 3.18 backport

Set ``CONFIG_EXT4_FS_POSIX_ACL`` to ``n`` in your defconfig.

.. _'patch ecryptfs to fix a build error' from bullhead: https://github.com/usb-bullhead-ubuntu-touch/kernel_msm/commit/b0403f0ee02e6582017cdb45b4c0c72b00cc72eb
.. _nick kvfree() from apparmor: https://github.com/ubports/android_kernel_moto_shamu/commit/83f949a8de673fe45499d1741da8654831a5afae
.. _Finish implementation of PID namespace: https://github.com/Halium/android_kernel_lge_hammerhead/commit/bd221854de33b75db7a7fa01cb34274b62a7cbf8
.. _perf\: Clarify perf_cpu_context\:\:active_pmu usage by renaming it to \:\:unique_pmu: https://github.com/Halium/android_kernel_fairphone_msm8974/commit/99bdb252098c1b926d3c851efbd70ab574d10a2c
