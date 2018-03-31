
Graphics
========

Graphics is an essential part of Halium. Halium uses libhybris to make Android's bionic based hardware adaptations layer usable with glibc systems.

Tests
-----

Here is some tests to test the graphics stack

.. code-block:: guess

   EGL_PLATFORM=hwcomposer test_hwcomposer

.. code-block:: guess

   test_egl

.. code-block:: guess

   test_egl_config

.. code-block:: guess

   test_glesv2

.. todo::
    Add tests using more heavy graphics applications using Wayland (mir)

Common errors
-------------

EGL_BAD_SURFACE
^^^^^^^^^^^^^^^

If these tests fail but some others succeed (lights, vibrator, Wi-Fi), you may need software which is built for Code Aurora Forum's Android for MSM (generally nicknamed "CAF" for short) rather than AOSP.

If this is the case, you'll errors similar to the following in :ref:`logcat`::

   W Adreno-GSL: <gsl_ldd_control:475>: ioctl fd 8 code 0xc0140933 (IOCTL_KGSL_TIMESTAMP_EVENT) failed: errno 22 Invalid argument
   W Adreno-GSL: <ioctl_kgsl_syncobj_create:2984>: (9, 1, 62845) fail 22 Invalid argument
   W Adreno-EGLSUB: <SwapBuffers:1339>: gsl_device_3d_add_fence_event failed
   W Adreno-EGL: <qeglDrvAPI_eglSwapBuffers:3890>: EGL_BAD_SURFACE

On the reference rootfs, you can get this software from the Halium repository by running the following commands::
   
   . /etc/environment
   echo "deb http://repo.halium.org/caf xenial main" >> /etc/apt/sources.list.d/halium-caf.list
   apt -get update
   apt-get dist-upgrade

Non-reference distributions will need to provide software which is compatible with CAF Android trees.

Reading pm4 microcode failed
----------------------------

This error may appear in :ref:`logcat` when running these tests::

   kgsl kgsl-3d0: |_load_firmware| request_firmware(a330_pm4.fw) failed: -2 … kgsl kgsl-3d0: |adreno_init| Reading pm4 microcode failed a330_pm4.fw

To resolve this, toggle ``CONFIG_FW_***LOADER`` in your kernel config.
