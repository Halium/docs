# How can i help get device x ported without coding skills?

**DISCLAIMER: this is still a work in progress and some parts are missing, however this will change soon and you can use it as it is for now**

Okay, we'll assume that you want to help in other ways than donating, bug reporting/testing, translating or organizing/moderating but instead **want to document**.

Why is this useful? If you have device x at home and want to have a working UBports (Ubuntu Touch)/KDE Mobile/Halium image but there is no developer out there right now who wants to take on this project you might think _I’ll just post a request in the forum, i can't do anything anyway_ but **that's wrong**. If you gather information about **software support (Cyanogenmod/Lineage OS/Android images and Kernels available)** what **Hardware is inside exactly**. You have already done the first steps and some dev might think he/she gives it a quick look.

If you now compare the exact hardware with existing, ported devices you **may find that most/some of the hardware is already supported on another device**. If this is the case, you can go a step further and try to find out where exactly in the code these hardware parts are mentioned and if they are also included in the so called 'mainline' linux kernel.

You think **this sounds hard and as if you need dev skills**? We will try to help you take this steps without any starting knowledge! (Okay you may need be able to search the web and write things into this wiki but we'll **do it together step by step below**.

For all those who read this but have a little more knowledge about some step/want to use different editors or tools to get to the end: This guide will **only show one way and no alternatives at all for better clarity for beginners** (for example, you can edit this wiki with many editors but we will recommend boostnote for now). There will also be nothing about github accounts, pull requests or anything but rather an approach that inexperienced users can do themselves. A and one final thing, some points are simplified to a great extend so don't take anything too literal!

## 1 First step: You wonder if you want Halium running on your device

You are on the right track! Halium offers the possibility to run Ubuntu Touch/KDE mobile and in the future perhaps even more cool distributions which are great ;-P. Let's see what we can do to make this dream come true...

  1. Check the [Device Overview Wiki Page](device_overview.md) if your device has already been inserted
  2. If it is **inside the list** BUT has no image for download available based upon Halium, see if the entry has all points covered or if info is missing. Also check the device specific sub page and the hardware parts' sub pages if there is some info that has not been inserted yet. Even if all those exist, try to check _when_ the info has been gathered, perhaps something has changed since then?
  3. If it is **NOT in the list** had over to the next sections to change this outrageous situation!

## 2 Second step: Get ready to document yourself

  1. Getting the current wiki & templates for all sites we want to create

Head over to the [github/Halium/docs](https://github.com/Halium/docs), click on the green button **download or clone** and select _Download ZIP_ from the drop down and unpack it in a folder of your choice and move to the folder "supplementary". Inside there are a few files of interest for us:
  * **Devices_Overview.md** here we will insert a quick list of the status of the device and link to a new device specific sub page we will create
  * **New_Device_Template.md** this will be our device template, that means we will copy this file, rename it to match our device name and fill the specific info about it

You can open each of these in a multitude of editors but the simple **gedit** which is pre-installed on Ubuntu suffices.

If we will go deeper later on, we might have to create chip-specific sub pages as well and edit the 'Hardware and Kernel Enablement' page but don't worry about this for now.

## 3 Third step: Editing the Devices_Overview.md

  1. Open up your browser of choice and head over to the [Device Overview Wiki Page](device_overview.md) again. You can use this for reference while editing it locally on your PC and also there is some useful links there that may lead you to the places where you find info about your device without opening it yourself.
  2. Also open Devices-Overview.md in gedit
  3. Then, just fill in the voids in the editor. Once finished you can save your work send in your changed Devices_Overview.md to docu@ubports.com THIS MAIL ADRESS NEEDS TO BE FIXED!
  4. Wait until someone merged it into the official wiki

**Note**:Alternatively, you can also create a github account, fork the wiki and create a pull request once you have edited everything you wanted in your branch. How this is achieved will be documented in a future post. But it is not that hard, you can find a quick interactive intro for git [here](https://try.github.io/levels/1/challenges/1) (it will take ~15 minutes)

## 4 Fourth step: Creating the specific Device_x.md

**// TODO: create reference_device.md //**

  1. Open up your browser and head over to the [showcasing page for device specific pages](reference_device.md). This will again be our references and may provide some useful links as well.
  2. Also open up the _New_Device_Template.md_ file with your editor and directly save-as _Your-Device-x.md_ so you always change the correct file and not the template
  3. Now look into the showcase and try to gather as much info about your device in the same style, save your work and submit in the same way as in step 3

Okay, by now you may have noticed it's not that hard, it's just a lot of work to do this. You may also notice that **if info is gathered in a centralized manner, devs may save lot's of time! so hurray to us and let's document a little bit more!**

## 5 Fifth step: Checking hardware enablement status

So this needs a very short intro: Every chip you might imagine that is inside your device needs a driver. This driver needs to be inside the so called _kernel_ which is the core of every Android/GNU linux system. There is the **mother of all kernels**, the so called _mainline kernel_ which is worked on by thousands of people all over the world. 

If all code (= all drivers) needed to run a device is inside this mainline kernel, it will stay there and other people will also take care about not destroying anything when a new version is developed and we can just use every new version that comes along. This kernel changes, sometimes in very radical steps which is why a driver that was once included in a custom kernel, let's say kernel 3.4-mydevice can't just be copied to 4.11 into the same directory. If we stick to a custom kernel, our little team needs to put all the new, sometimes radical changes into our custom kernel which is much more work on much fewer shoulders in comparison to mainlining our little device specific code.

The biggest issue however is not that the kernel changes but rather **that manufacturers include code that cannot be read or changed by us (legally)** (so called proprietary _blobs_). Which is why we are often stuck at older kernel versions. BUT the **community is often developing alternative free and open source drivers** to replace these blobs. At a certain point, it is possible to 'suddenly' run a device with a new kernel (for example the Nexus 7 2013 is step-by-step mainlined by John Stultz and others). **Our porting devs cannot watch the kernel all the time so we as community can try to check which hardware is supported how well**.

Also, we can link to older, working kernels and where inside of them the specific drivers sit. Some day someone might have the time to take a look and then only needs to look up the paths we provide instead of searching themselves.

So what to do:
  1. Open up your browser and head over to the  [Hardware and Kernel Enablement](hardware_enablement.md) page.
  2. Open up the same page in your editor
  3. Insert missing info and submit your changes
  4. If you find a part without it's own sub page, you might want to create one, head over to Step 6 for that!

## 6 Sixth step: Adding new hardware parts

** // TODO: add component_template.md//**

If there is no sub page for a certain hardware component (e.g. a Wifi + Bluetooth chip) you can also create a new hardware component sub page from the template. Just open up the _New-component-template.md_ file, save as _Your-component.md_, fill with info and submit to the docs team.