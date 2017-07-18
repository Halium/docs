# supplementary hardware information

## What to document here?
In this section, we want to gather information about 
 * the exact hardware built into our phones and tablets
 * the software status for these devices, that is:
   * which OS is available in what version and to which degree of functionality
   * which kernel is available? What drivers are used for what part?
   * where are the sources for all this? What is their license?
 * where can we reuse drivers/kernel patches/backports 
 
## Where to document this?
The documentation should preferably have a logical structure so that every specific group of devs we are trying to help here can access the info that is meant for them without having to read the other parts.
 * [Device Overview](device_overview.md) this is meant for linking to each devices sub page, show halium status (for porters) and list exact hardware parts (for kernel devs)
 * [Hardware Enablement](hardware_enablement.md) this is more or less only for the kernel devs and should document mainlining/driver progress for all the hardware
 * [How 2 Document](how_2_document.md) this is only for newcomers who want to know how to help with documenting here

## Why is this important?

Halium is trying to reduce the workload for different OS teams by developing a common base. The deepest root in all of the OS systems, even the official ones, is the kernel, which is based upon the linux mainline kernel. For Halium to work, certain features need to be implemented into this kernel, for example the ability to use lxc.

Therefore it is of great interest to us to have a kernel for each device that has all the needed parts. The sense behind mainlining is that **you only care about the specific hardware you are working on**. All other features that are implemented by other people will just be handled mainline and if your code is mainline too, upon a kernel update, you can just use the new one with new features from other people, without having to reimplement your driver into this new kernel. So if e.g. lxc is updated or apparmor and we are working on an older kernel, at some point the rootfs we are working with will require this new version and we need to do all the implementation of our work to a new kernel.

By documenting things **that will never change** like the hardware built into a phone, the kernel version a driver was mainlined or general mainline status of hardware parts, we reduce the risk to document something that will change before it is ever looked at.

On the other hand, comparing the hardware of devices shows, that many parts are used across manufacturers, so many drivers may, at least partially, be cloned. 

With documenting these things at a central point, we may make connections easier visible and by this enable kernel devs or newcomers to write/modify drivers and mainline them.

For our porters, we can gather info about available Android/Lineage/Cyanogenmod/... versions, where the sources and if available proprietary blobs are located and perhaps what challenges/problems may occur if any are known already.

## Who is this for?

This sub section of the documentation is meant for

 * **porters** as a first quick reference about the status for certain hardware parts (drivers) and whole devices (custom kernels & OSes)
 * **community members** who want to help by documenting
 * **kernel devs** as a reference which hardware is in what device, if there are open source drivers or where the official drivers are located

