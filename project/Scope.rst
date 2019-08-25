Scope of Halium
===============

Halium's scope primarily consists of 2 parts:

1. Halium's Android is a minimal Android distribution designed to run within an LXC container. It will provide a set of interfaces to let the host of the LXC container utilize Android's HAL to communicate with the hardware of Android-based smartphones. These interfaces come in 3 forms:

    1. Native Android interfaces. In this category, the interface is used either unmodified or with only the standard libhybris wrapper. For example, this includes rild's socket, Audio HAL (dlopen'ed directly), and WiFi HAL (`a standard libhybris wrapper <https://github.com/libhybris/libhybris/tree/master/hybris/wifi>`_).
    2. Libhybris compat layer. Usually used to wrap Android C++ interfaces, contains some logic, and has its counter-part compiled in the Android tree. An example is the `HWC2 compat layer <https://github.com/libhybris/libhybris/tree/master/compat/hwc2>`_ in libhybris.
    3. Custom interfaces. This will contain more than a compat layer and may have quite deep integration within Android code. We would like to reduce this kind of interface as much as possible to reduce our workload, especially those doing deep modification to Android. An example would be the Ubuntu Touch's camera interfaces, which consists of `camera compat layer <https://github.com/libhybris/libhybris/tree/master/compat/camera>`_, `custom media compat layer <https://github.com/libhybris/libhybris/tree/master/compat/media>`_, and deep modifications to Android's libmedia [1]_.

2. Halium's middleware is a set of software, libraries, and Linux kernel modules which talk to the interfaces in (1.). It is mostly distro and toolkit agnostic. For example, this includes `pulseaudio-module-droid <https://github.com/mer-hybris/pulseaudio-modules-droid>`_, but will not include `qtubuntu-camera <https://github.com/ubports/qtubuntu-camera>`_ (the client of the aforementioned camera interface, as it's tied to Qt). Halium may not be upstream of most of the middlewares. Thus, most of the time we'll just maintain the minimal patch(es) that make them work in Halium-based environment.

Halium will primarily be a source-only distribution. Downstream distributions (such as Plasma Mobile or Ubuntu Touch) can modify the Android distribution for their needs. The modified Android can then be built and provided as part of their distribution. For example, Ubuntu Touch adds `platform-api <https://github.com/ubports/platform-api>`_ and additional kernel parameters to enable AppArmor, then provides Android images as part of its OTA update model.

Halium will provide the reference rootfs to demonstrate how to integrate Halium intro distributions and help porters develop their port. It'll contain the common middlewares and enough testing tools to help determine if the port is likely to work in more full-blown distributions or not. A reference repo, which is primarily used to build the reference rootfs, will also be provided. Downstream distributions can use this repo but are not required to.

Reference-implementation only components
----------------------------------------

There are components which require tight integration with distributions, for example:

  - Deployment tools
  - Initramfs tooling
  - Scripts used in Linux userspace for the boot sequence (systemd units, init.rc scripts, etc.)

We understand that every distribution has its own requirements for these tools, so they are not enforced. We provide reference implementations of each of these which may or may not be used by downstream distributions. For example:

  - Deployment tools: `Halium-install <https://gitlab.com/JBBgameich/halium-install>`_
  - Initramfs: `Hybris-boot <https://github.com/Halium/hybris-boot>`_ or `Halium-boot <https://github.com/Halium/halium-boot>`_
  - Boot sequence scripts: `lxc-android <https://github.com/Halium/lxc-android>`_

.. [1] The modification makes changes to audio handling of libmedia to make video recording accept audio from Pulseaudio via UNIX domain socket. This is tightly integrated with how qtubuntu-camera works. See https://github.com/ubports/android_frameworks_av/compare/1516fdb...c66dd36
