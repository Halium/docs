
Development
===========

Development plan/outline:
-------------------------

*Goal:* being able to ``adb shell`` / ``telnet`` / ``SSH`` into the ``GNU/Linux`` system where you can run tests related to ``android`` hardware enablement and they work out of the box.

*Reference device(s):* ``Nexus 5``\ , ``Oneplus one``\ , ``Nexus 5X`` (It will be interesting to see how easy it makes it for ``Ubuntu Touch`` once ``Halium`` works for this device).

*Reference rootfs:* ``Ubuntu ARM`` or ``ArchLinux ARM`` or ``Debian ARM`` or ``Fedora ARM`` (Requirement: ``systemd`` as main init system)

Initial development (stage 0, libhybris):
-----------------------------------------


* [ ] Fork the Android source tree with libhybris patches
* [ ] Bring continuous integration system up to build the android image
* [ ] Start with the basic rootfs (ubuntu 16.04)
* [ ] Build and integrate the libhybris (upstream) to the base rootfs
* [ ] Create publishing infrastructure for the distribution of the android image and rootfs
* [ ] At this point it's fine if not all tests "pass" but they should at least run.

Hardware enablement (stage 1):
------------------------------


* [ ] After stage 0 we will have a system to work on where we are able to run the ``libhybris`` tests and get the logs required, in this stage we can pick random hardware component and get it working
* [ ] At end of this stage, Halium is "ready" for distributions

Device enablement (stage 2):
----------------------------


* [ ] During this stage we will have most of the infrastructure ready for including new devices, so this is the time to go wild ;-)

*Tests:* We need to write tests that can run in our reference rootfs to make it easier to spot problems, we need both direct tests that live in ``android`` and tests that use ``libhybris``.

*Automated tests:* These tests will run run after each ``CI`` build to ensure the builds that comes out of our build servers are working. (@UBports has some tests we can use for this)

Future ideas
------------


* [ ] Common upstream msm kernel for all devices
* [ ] Common sets of qcom drivers
* [ ] All qcom devices to caf
* [ ] Freedreno for mainlined devices
* [ ] Backport 5.1 and 6.0 kernel driver required by 5.1 and 6.0 blobs
* [ ] Upstream the Android N port of libhybris from UBports fork
* [ ] Common place to put device configs for userspace (not talking about android device configs here, but the config each OS uses to configure different parts)
* [ ] Create a *translator* that converts common configs to OS specific configs
* [ ] Possibly something to "update" kernel from distribution packaging. I remember @mickybart/gnulinux_support has something around that.
* [ ] Create a sandbox env to test *only* the hal and libhybris
