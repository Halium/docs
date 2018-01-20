
How to contribute documentation
===============================

**DISCLAIMER: this is still a work in progress and some parts are missing, however this will change soon and you can use it as it is for now**

Okay, we'll assume that you want to help in other ways than donating, bug reporting/testing, translating or organizing/moderating but instead want to document.

Why is this useful? If you have device x at home and want to have a working UBports (Ubuntu Touch)/Plasma Mobile/Halium image but there is no developer out there right now who wants to take on this project you might think *I’ll just post a request in the forum, I can't do anything anyway* but **that's wrong**. If you gather information about **software support (Cyanogenmod/Lineage OS/Android images and Kernels available)** what **Hardware is inside exactly**. You have already done the first steps and some dev might think he/she gives it a quick look.

If you now compare the exact hardware with existing, ported devices you **may find that most/some of the hardware is already supported on another device**. If this is the case, you can go a step further and try to find out where exactly in the code these hardware parts are mentioned and if they are also included in the so called 'mainline' linux kernel.

You think this sounds hard and as if you need dev skills? We will try to help you take this steps without any starting knowledge!

For all those who read this but have a little more knowledge about some step/want to use different editors or tools to get to the end: This guide will only show one way and no alternatives at all for better clarity for beginners (for example, you can edit this wiki with many editors but we will recommend typora for now). There will also be nothing about github accounts, pull requests or anything but rather an approach that inexperienced users can do themselves. A and one final thing, some points are simplified to a great extend so don't take anything too literal!

Check for existing Halium work
------------------------------

1. Check the :doc:`devices/index` page to see if your device has already been inserted
    1.  If it is **inside the list** BUT has no image for download available based upon Halium, see if the entry has all points covered or if info is missing. Also check the device specific sub page and the hardware parts' sub pages if there is some info that has not been inserted yet. Even if all those exist,  the info has been gathered, perhaps something has changed since then?
    2. If it is **NOT in the list**, continue to the next section


Download templates and files
----------------------------

1. Getting the current wiki & templates for all sites we want to create

Head over to `this documentation's GitHub repository <https://github.com/Halium/docs>`_, click on the green button **download or clone** and select *Download ZIP* from the drop down and unpack it in a folder of your choice and move to the folder "supplementary/devices". Inside there are a few files of interest for us:

* **index.rst** here we will insert a quick list of the status of the device and link to a new device specific sub page we will create
* **devicetemplate.rst** this will be our device template, that means we will copy this file, rename it to match our device name and fill the specific info about it

You can open each of these in a multitude of editors but the simple **gedit** which is pre-installed on Ubuntu suffices.

If we will go deeper later on, we might have to create chip-specific sub pages as well and edit the 'Hardware and Kernel Enablement' page but don't worry about this for now.

Edit device-overview
--------------------

1. Open up your browser of choice and head over to the :doc:`devices/index` again. You can use this for reference while editing it locally on your PC and also there is some useful links there that may lead you to the places where you find info about your device without opening it yourself.
2. Also open index.rst in gedit
3. Then, just fill in the voids in the editor. Once finished you can save your work send in your changed index.rst to docu@ubports.com THIS MAIL ADRESS NEEDS TO BE FIXED!
4. Wait until someone merged it into the official wiki


**Note**\ :Alternatively, you can also create a github account, fork the wiki and create a pull request once you have edited everything you wanted in your branch. How this is achieved will be documented in a future post. But it is not that hard, you can find a quick interactive intro for git `here <https://try.github.io/levels/1/challenges/1>`_ (it will take ~15 minutes)

Create device documentation
---------------------------

.. todo::
  create reference-device.rst

1. Open up your browser and head over to the :doc:`template for device specific pages <devices/index>`. This will again be our reference and may provide some useful links as well.
2. Also open up the **devicetemplate.rst** file with your editor and directly save-as *Your-Device-x.rst* so you always change the correct file and not the template.
3. Now look into the showcase and try to gather as much info about your device in the same style, save your work and submit in the same way as in step 3.

Okay, by now you may have noticed it's not that hard, it's just a lot of work to do this. You may also notice that if info is gathered in a centralized manner, devs may save lot's of time!

Check hardware enablement
-------------------------

So this needs a very short intro: Every chip you might imagine that is inside your device needs a driver. This driver needs to be inside the so called *kernel* which is the core of every Android/GNU linux system. There is the **mother of all kernels**\ , the so called *mainline kernel* which is worked on by thousands of people all over the world. 

If all code (= all drivers) needed to run a device is inside this mainline kernel, it will stay there and other people will also take care about not destroying anything when a new version is developed and we can just use every new version that comes along. This kernel changes, sometimes in very radical steps which is why a driver that was once included in a custom kernel, let's say kernel 3.4-mydevice can't just be copied to 4.11 into the same directory. If we stick to a custom kernel, our little team needs to put all the new, sometimes radical changes into our custom kernel which is much more work on much fewer shoulders in comparison to mainlining our little device specific code.

The biggest issue however is not that the kernel changes but rather **that manufacturers include code that cannot be read or changed by us (legally)** (so called proprietary *blobs*\ ). Which is why we are often stuck at older kernel versions. BUT the **community is often developing alternative free and open source drivers** to replace these blobs. At a certain point, it is possible to 'suddenly' run a device with a new kernel (for example the Nexus 7 2013 is step-by-step mainlined by John Stultz and others). **Our porting devs cannot watch the kernel all the time so we as community can try to check which hardware is supported how well**.

Also, we can link to older, working kernels and where inside of them the specific drivers sit. Some day someone might have the time to take a look and then only needs to look up the paths we provide instead of searching themselves.

So what to do:

1. Open up your browser and head over to the :doc:`hardware-enablement` page.
2. Open up the same page in your editor (**supplementary/hardware-enablement.rst**)
3. Insert missing info and submit your changes
4. If you find a part without its own subpage, you might want to create one. Head to the next step for that.


Create pages for undocumented hardware
--------------------------------------

.. todo::
  add component_template.rst

If there is no sub page for a certain hardware component (e.g. a Wifi + Bluetooth chip) you can also create a new hardware component sub page from the template. Just open up the *New-component-template.rst* file, save as *Your-component.rst*\ , fill with info and submit to the docs team.
