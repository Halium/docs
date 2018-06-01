Install Halium
==============

At this point, you've set up your build device, downloaded all of the sources for device enablement, and built ``hybris-boot.img`` and ``system.img``. Now, we'll walk you through installing your build along with a distro.


Fully halium-integrated distributions
-------------------------------------

You may choose any of the following distributions to install with the scripts and sources provided by Halium. We recommend you start with the reference rootfs for testing.

.. toctree::
   :maxdepth: 1
   
   reference-rootfs

.. todo::
   Add instructions for installing Plasma Mobile


Halium-modified distributions
-----------------------------

These distributions require changes to the source or use different scripts than those provided by Halium. We recommend you only try these after your build tests correctly with the reference rootfs.

.. toctree::
   :maxdepth: 1
   
   Ubuntu Touch <https://docs.ubports.com/en/latest/porting/introduction.html>

.. todo::
   Distributions like Ubuntu Touch and LuneOS go here. Links to their respective documentation should be sufficient, but please place them inside the toctree above.
