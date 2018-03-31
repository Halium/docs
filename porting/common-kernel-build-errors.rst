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