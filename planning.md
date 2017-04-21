# Linux kernel + Android + Libhybris common basel

## Introduction

Overall idea is, This stack includes,

*   Linux kernel

*   Android HAL

*   Sensors

*   Camera

*   RILd

*   Libhybris

*   Android HAL interfaces like Audioflingerglue and droidmedia

*   Build system and scripts

*   GPS - AGPS from Mozilla

*   Pulseaudio

*   Media codecs

*   oFono

*   Way to distribute updates and images (way to install) (that's debatable)

*   Systemd? (Upstart can handle user-level service initialization: See Ubuntu Touch)

This stack doesn't include the,

*   Qt

*   No Qt would be best, most platforms are very strict on the version they depend on

*   Wayland

*   KWin hwcomposer platform

*   Plasma

*   Unity

*   Mir

*   Lipstick

*   Gecko

*   Applications

*   ....

## Action Points

*   Have a team meeting​ possibly this week(?)
*   See if there are any conflicting requirements and how best to resolve them. For eg. Ubuntu touch needs apparmor patches in kernel, while Sailfish doesn’t.
*   Decide what the stack will contain and make a short summary of the whole thing.
*   Make a proposition for Sailfish OS, Open Source, community collaboration meeting at #mer-meeting@freenode. Add a new topic to the agenda [here](https://together.jolla.com/question/54157/sailfishos-open-source-collaboration-meeting-planning/). Action by:<name></name>
*   Decide how the lxc/container should be setup (img file like ubuntu or in rootfs like sailfish)
*   Decide what will be the default method to accrue android, build our own or take vendors and modify that (both would be best here in my opinion)
*   What infrastructure we will need for this? What are options?
*   Fork [https://github.com/mickybart/gnulinux_support](https://github.com/mickybart/gnulinux_support) / make pull requests?
*   Find all kernel features systemd requires, maybe fork mer-kernel-check to automatically check kernel configs
*   Fork [https://github.com/ubports/ubports-installer](https://github.com/ubports/ubports-installer) for cross platform installations
*   Fork ubp-5.1 && ubp-7.0
*   Common support for Multirom :) YES PLEASE I don’t think Multirom is maintained anymore, but we can fork it can continue it ; There’s already a fork with active developers: [https://github.com/multirom-dev](https://github.com/multirom-dev)
*   Please let’s move away from android recovery update method (it does not fit us) (Boot from sdcard using efidroid at least for testing, so write images to sdcards?)
*   Document all the things! YES! We need that badly

## Feature ideas

*   Common upstream msm kernel for all devices

*   Common sets of qcom drivers

*   All qcom devices to caf

*   Freedreno for mainlined devices

*   Backport 5.1 and 6.0 kernel driver required by 5.1 and 6.0 blobs

*   Upstream the Android N port of libhybris from UBports fork

*   Common place to place device configs for userspace (not talking about android device configs here, but the config each OS uses to config different parts)

*   Create a _translator_ that convert common configs to OS specific configs

*   Possibly something to “update” kernel from distribution packaging. I remember gnulinux_support have something around that.

*   Create a sandbox env to test _only_ the hal and libhybris

*   Mentioning Flatpak, Snappy as target platforms is important

*   (what about others like appimages? You can basically run every type of package on this base)

*   appimage cannot possibly be supported by a platform, by definition. But sure, it’s not about excluding anyone.

*   Also note it’s not the same to support bundles than packaging systems. Packaging systems cannot work.

## Name

Since we can’t call ourselves Libhybris, we should think of a nice name for this. Suggest your names in the list below. Add a (+1) (+2) etc. to the one you like. (Maybe do that on strawpoll?) (need comments too)

*   Stroqdu
*   OpenPhablet (+2) (may be confusing, phablets aren't the only target) < phablets are not even a thing, we should think convergence
*   OpenDroid(Hal) (-1, this would be confusing) (+1)
*   GnuDroid (+1)
*   Mobile Linux Standard Base (MLSB)
*   Libre Device Platform
*   Linux Compatibility Platform (+2)

The name should be inclusive enough so anyone in the FOSS world feels identified by it, they should read the name and know it belongs in their pocket.

Maybe something that doesn't associate with Droid? (+7)

*   Open::hal
*   Open::phablet
*   LibreBase
*   Halogen (+1)
*   Halygon
*   Halium (+10) (-1)
*   Integra

![](images/image00.png)

*   Hydra (+1)

Mer-meeting

bhushan

Dinesh

Mariogrip

Toxip will setup outline for meeting

* * *

# REVIEW ONCE THEN MOVE UP - bshah

## What this base consists of? Or what is our “products”?

*   AOSP source tree (LineageOS)
*   Collection of Device Repos (similar to Cyanogenmod)
*   Prebuilt and ready-to-integrate android images
*   Reference packaging of libhybris and co. for the distributions / developers
*   Reference binary images of this stuff
*   Tool to flash the images
*   Documentation on how to integrate the AOSP base with Linux system (this is most important.. Basically everything we create needs to be documented from start)
*   Common config system?

What I would expect from this is a minimal booting android with libhybris, and all the libhybris tests pass

## What is the lifecycle of port?

*   Porting team decides upon target (or someone suggests it)
*   We create android device and vendor tree or “fork” it from LineageOS/CM/AOSP/whatever
*   Integrate our changes required for libhybris etc
*   CI builds image and publishes them

## Distributions (Plasma Mobile, UBports, Mer etc)

*   Distributions picks up this new packaging if they are using our reference packaging for userspace (Linux) parts, otherwise they build their own packages.
*   Along with rootfs generated from side of Distribution, they use the android IMG from the port lifecycle. (kernel depends on splitting / not splitting android and kernel)

# PLEASE REVIEW, THEN MOVE UP - JBBgameich

## Different ways of starting android - pro and cons

1.  ## Split kernel and Android and start up android system services and the normal system using systemd and for example droid-hal-init, or start up a android chroot

### Pro

*   The glibc based linux runs “more native”
*   Full control about the boot process
*   Cleaner for long term (when mainlined devices exist which don’t need android things)

### Con

*   Requires a real build script

### 1.1) Run android inside a container or schroot

### Pro

*   maybe more secure
*   Android and glibc linux cannot conflict
*   fewer modifications to the Android side are needed (If android init is run inside a chroot), thereby easier upgrading.

### Con

# The Stack - proposal

The system is running on a android manufacturer linux kernel, IF the device is mainlined, it can run mainline linux kernel

(Initramfs?)

Systemd start’s up the system and the android HAL, which runs either in a schroot, container, or directly on the system.

Graphic output, camera and other sensors are managed by libhybris.

The linux distribution running with this stack can either use packages of libhybris etc. offered by us, if it’s compatible, or build it’s own

![halium_architecture.svg55d72.png](images/image01.png)

Hello everyone,

To introduce, I am Bhushan Shah from KDE, Plasma Mobile maintainer and in CC:  
Marius Gripsgård, is founder and maintainer of project UBports, Toxip is part of  
Sailfish OS Fan Club group on telegram.

Earlier it was suggested to our projects that we should collaborate with other  
communities working on making GNU/Linux available to android phones, and that  
idea made lot of sense to us. Below is some details about the current situation  
and how this idea aims to solve it.

Currently Ubuntu Touch, SailfishOS/Mer, Plasma Mobile and others have  
different android source trees and methods on how our stacks are built. There is  
lot of fragmentation on the following areas:

*   Android source tree
*   How android init is started (droid-hal-init vs lxc container vs chroot  
    etc..)
*   How images are flashed to device, (flash cm first v/s flash system directly)
*   ...

But ideally these parts wouldn’t need to be separate, because we all have the  
same goal in the end. Each OS make use of android binary drivers using projects like  
libhybris, ofono, libcamera, audioflinger glue etc.

Instead of being fragmented and everyone having to do the same job in a different way we have come up with idea to have a common base for all the OSs. The common base would include Linux kernel + Android HAL + libhybris shared between all the OSs. Less fragmentation would mean more common resources and would be a huge boon for porting efforts.

This kind of approach would have the following benefits:

*   Shared porting effort, port once and use everywhere
*   More streamlined HAL
*   Makes it easier for other distributions to run on mobile devices
*   Common ground for communication between the different projects

Currently this project idea is codenamed Halium. Overall idea for the project is drafted at the  
[https://tinyurl.com/halium](https://www.google.com/url?q=https://tinyurl.com/halium&sa=D&ust=1492799339891000& usg=AFQjCNEq5Y4Ntg8lvQjuGKm0IY5h842YVQ) , and our communication channels are at matrix channel

# halium:disroot.org or at IRC channel #halium@freenode or at telegram group

[https://t.me/halium](https://t.me/halium) . (All of these communication channels are bridged  
together, so you can choose whatever suits the best for you).

If you’re interested in this kind of collaboration or have any comments or questions, please join one of our communications channels or reply to this message. We will be happy to answer to any kind of questions.

We are looking forward to your feedback and collaboration.  
The Halium team

* * *

## Development plan/outline:

Goal: being able to adb shell / telnet / SSH into the Linux system where you can run tests related to android hardware enablement and they work out of the box.

Reference device(s): Nexus 5, Oneplus one, Nexus 5X (It will be interesting to see how easy it makes it for Ubuntu Touch once halium works for this device).

Reference rootfs: Ubuntu ARM or ArchLinux ARM or Debian ARM or Fedora ARM (Rerquirement: probably systemd as main init system).. or whatever :P

Initial development (stage 0, libhybris):

*   Fork the android source tree with libhybris patches
*   Bring continuous integration system up to build the android image
*   Start with the basic rootfs (ubuntu 16.04)
*   Build and integrate the libhybris (upstream) to the base rootfs
*   Create publishing infrastructure for the distribution of the android image and rootfs
*   At this point it’s fine if not all tests “pass” but they should at least run.

Hardware enablement (stage 1):

*   After stage 0 we will have system to work on where we are able to run the libhybris tests and get the logs required, in this stage will pick random hardware component and get it working
*   At end of this stage, halium is “ready” for distributions

Device enablement (stage 2):

*   During this stage we will have most of infrastructure ready for including new devices, so this is the time to go wild ;-)

Tests: We need to write tests that can run in our reference rootfs to make it easier to spot problems, we need both direct tests that lives in android and tests that uses libhybris.

Automated tests: These test will run run after each CI build to ensure the build that comes out of our build servers are working. (ubports has some tests we can use for this)

* * *

## Some random links

*   [http://www.webos-ports.org/wiki/Halium_Considerations](http://www.webos-ports.org/wiki/Halium_Considerations)

*   [http://merproject.org/meetings/mer-meeting/2017/mer-meeting.2017-04-19-08.00.txt](http://merproject.org/meetings/mer-meeting/2017/mer-meeting.2017-04-19-08.00.txt)

*   [http://merproject.org/meetings/mer-meeting/2017/mer-meeting.2017-04-19-08.00.log.html](http://merproject.org/meetings/mer-meeting/2017/mer-meeting.2017-04-19-08.00.log.html)

## Mer-meeting takeaway

Jolla guys potentially interested but too early to commit to this. We need a proper proof-of-concept to show mer could run on top. Sailfish OS community devs of course anyone is welcome.

Jolla was concerned about how our things work with the ODMs way of things. This may not be a problem for community projects like ubports, plasma, et. al. but especially for Jolla since they’re dealing straight with the ODMs. Something to take into account when we build our infrastructure. We should make it as flexible as possible so that this would work with them also.

## FAQ

Why this effort?

Who are you?

* * *

## Agenda for next meeting

*   Going public

*   Website [Halium.org repository](https://github.com/Halium/halium.org)

*   initial announcement

*   individual announcement (i.e on ubports, pm blog?)

*   Development

*   Proposed stage 0 development plan

*   Creating todo items from action points

*   Use github as task tracker(?)

*   What infrastructure we need

*   Image build node

*   rootfs build node (probably both can be combined)

*   place to serve the images

*   documentation website

*   do we have sponsor for this? can we reuse our own infrastructure (ubports/pm/sailfishos) for while?

*   Team management

*   Who wants to volunteer and which parts

*   Development

*   Porting

*   Documentation

*   Testing

*   Communication

# Initial halium creator script (locusf rambling)

1.  Plug in phone, run adb, which pulls in needed binaries from /system
2.  builds halium kernel + the boot selection (still wondering what this could be)
3.  boot selector then fetches/runs the actual os inside some runtime (container/switch_root up to debate)

*   ![](images/image02.jpg "Seen by @yannic:mryr.de at 2:16:00 PM")

Halium kernel means both the actual kernel + middleware needed in order to have a common libhybris base from the running android system 
