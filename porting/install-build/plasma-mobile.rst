
Plasma mobile
=============

In order to install `Plasma mobile <https://www.plasma-mobile.org>`_ you perform basically the same steps as for the :doc:`reference-rootfs`. This section only highlights the relevant differences.

Install rootfs and system.img
-----------------------------

Use the plasma mobile rootfs. Download the latest version from here: `<https://images.plasma-mobile.org/rootfs/>`_.

If you have a "CAF" device (Code Aurora Forum), then you must use the rootfs from here: `<https://images.plasma-mobile.org/caf-rootfs/>`_. Generally speaking, if it is a Qualcomm device and it is not a Nexus, then it is CAF.


Debugging
---------

Instead of connecting with `root` you use `phablet`::

   ssh phablet@10.15.19.82

.. todo::
   Make sure phablet password is set either by using chroot from recovery or halium-install from `JBBgameich <https://github.com/JBBgameich/halium-install>`_.

For general debugging tips refer back to reference rootfs instructions. Some plasma mobile specific tips are below.

.. todo::
   Document PM specific debug instructions. Some lose notes copied from irc log:

   * run test_XYZ with sudo
   * pgrep kwin_wayland
   * journalctl | grep simplelogin

