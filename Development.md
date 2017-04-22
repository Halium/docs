## Development plan/outline:

*Goal:* being able to adb shell / telnet / SSH into the Linux system where you can run tests related to android hardware enablement and they work out of the box.

*Reference device(s):* Nexus 5, Oneplus one, Nexus 5X (It will be interesting to see how easy it makes it for Ubuntu Touch once halium works for this device).

*Reference rootfs:* Ubuntu ARM or ArchLinux ARM or Debian ARM or Fedora ARM (Rerquirement: systemd as main init system)

## Initial development (stage 0, libhybris):

- [ ] Fork the android source tree with libhybris patches
- [ ] Bring continuous integration system up to build the android image
- [ ] Start with the basic rootfs (ubuntu 16.04)
- [ ] Build and integrate the libhybris (upstream) to the base rootfs
- [ ] Create publishing infrastructure for the distribution of the android image and rootfs
- [ ] At this point it’s fine if not all tests “pass” but they should at least run.

## Hardware enablement (stage 1):

- [ ] After stage 0 we will have system to work on where we are able to run the libhybris tests and get the logs required, in this stage will pick random hardware component and get it working
- [ ] At end of this stage, halium is “ready” for distributions

## Device enablement (stage 2):

- [ ] During this stage we will have most of infrastructure ready for including new devices, so this is the time to go wild ;-)

*Tests:* We need to write tests that can run in our reference rootfs to make it easier to spot problems, we need both direct tests that lives in android and tests that uses libhybris.

*Automated tests:* These test will run run after each CI build to ensure the build that comes out of our build servers are working. (ubports has some tests we can use for this)
