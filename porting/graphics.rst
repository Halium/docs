
Graphics
========

Graphics is an essential part of Halium. Halium uses libhybris to make Android's bionic based hardware adaptations layer usable with glibc systems.

Tests
-----

Here is some tests to test the graphics stack

.. code-block::

   test_hwcomposter

.. code-block::

   test_egl

.. code-block::

   test_egl_config

.. code-block::

   test_glesv2

//TODO: add tests using more heavy graphics applications using Wayland (mir)
