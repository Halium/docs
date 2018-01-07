
Get Halium source
=================

Now that you have a target device selected and your build device ready, it's time to get the sources for your target together. Let's begin by initializing your source tree.


Create and initialize source tree
---------------------------------

Make yourself a new directory to put your Halium source in::

   mkdir halium && cd halium

This directory will be called BUILDDIR in the remaining part of the guide, when necessary, to avoid confusion.

If the target device has Android 7.1 or LineageOS 14.1 support, it's recommended to select ``halium-7.1``::

   repo init -u https://github.com/Halium/android -b halium-7.1

If your device does not have Android 7.1 or LineageOS 14.1 support but has support for Android 5.1 or CyanogenMod 12.1, select ``halium-5.1``\ ::

   repo init -u https://github.com/Halium/android -b halium-5.1

``halium-7.1`` is based on LineageOS 14.1

``halium-5.1`` is based on CyanogenMod 12.1


Adding your device-specific source
----------------------------------

Okay, so now you have the default manifest for Ubuntu Touch. This will enable you to download the basic Android sources used to build Ubuntu Touch, but you'll need to find device-specific files. These enable the build system to make Android for your device.

If there's any part for you to make a mistake on, this will be the one. Finding the files isn't hard, but it might take you a couple of tries to get repo's local manifest created correctly.

First, you'll want to find the repositories for your device on `LineageOS's GitHub organization <https://github.com/lineageos>`_. You can do this by typing your device's codename into the search box. You'll want the device repository, ``android_device_[manufacturer]_[device]``. Take down this name, as you'll need it later.

There will be a ``cm.dependencies`` or ``lineage.dependencies`` file in that repository that will tell you all of the other repositories that your device is reliant upon. Keep this file around as you will need it in a little bit.

Change into your Halium directory and create the directory ``.repo/local_manifests/``. Then, edit the file ``.repo/local_manifests/[manufacturer]_[device].xml``.

Paste the following into the file:

.. code-block:: xml
    
    <?xml version="1.0" encoding="UTF-8"?>
    <manifest>
    
    </manifest>

We recommend cloning all of the repositories that you'll find in the next steps to a personal source archive (aka, fork or import them on GitHub), then adding those personal forks to the manifest. This will help you save and share your work later.


The Device Repository
^^^^^^^^^^^^^^^^^^^^^

Next, we'll fill the manifest with information. Start with your device repository. Create the following line between the <manifest> and </manifest> tags, replacing the information inside the square brackets with your own:

.. code-block:: xml

    <project path="device/[manufacturer]/[device]" name="[repository name]" remote="[remote]" revision="[revision]" />
    
.. Note::

    The ``revision`` attribute may be omitted if the default revision for this remote is the one that you wish to use.

If you're not sure of your remote, jump down to `Remotes`_.


Dependencies
^^^^^^^^^^^^

Now create more lines like the previous, using the ``cm.dependencies`` or ``lineage.dependencies`` file you found earlier in your device repository. This file lists all of the other repositories that you need to build for your selected device. It's listed in a fairly straightforward way, so create a line for each of the entries in there using the following template:

.. code-block:: xml

    <project path="[target_path]" name="[repository]" remote="[remote]" revision="[revision]" />

The target path is found in the repository's name. The preceding "android" or "proprietary" is omitted and underscores are replaced with slashes. For example, ``android_device_lge_bullhead`` goes in ``device/lge/bullhead``.


Vendor blobs
^^^^^^^^^^^^

Vendor blobs go in the ``vendor/`` folder in your Halium source tree. You will need to find these in a repository or otherwise and add them to your source tree. Check if your device's vendor is listed in `TheMuppets' GitHub organization <https://github.com/TheMuppets>`_, then open the repository to see if your device's codename is inside on your desired branch.

If you are unable to find your device in TheMuppets, you will need to find another repository with the vendor files somewhere.


Remotes
^^^^^^^

A remote entry specifies the name, location (fetch) prefix, code review server, and default revision (branch/tag) for source.

You can create a remote by adding a ``remote`` tag to your manifest.

.. code-block:: xml

      <remote  name="aosp"
           fetch="https://android.googlesource.com"
           review="android-review.googlesource.com"
           revision="refs/tags/android-7.1.1_r25" />

Only the name, fetch, and revision attributes are required. The review attribute specifies a Gerrit Code Review server, which probably won't be useful for initial porting purposes.

For example, let's say that you have a bunch of repositories at ``https://github.com/MyUserName/`` and your desired branch name is ``cm-14.1`` in each. You would create a remote as follows and place it into your local manifest:

.. code-block:: xml

    <remote name="mun"
        fetch="https://github.com/MyUserName"
        revision="cm-14.1" />

These remotes are available to you by default:

===========  =======================
Remote Name  Remote Description, URL
-----------  -----------------------
aosp         Android Open Source Project, https://android.googlesource.com
los          LineageOS, http://github.com/LineageOS
hal          Halium (link to GitHub root for legacy reasons), http://github.com
them         TheMuppets, http://github.com/TheMuppets
===========  =======================

If you do not specify a remote, ``aosp`` is assumed. See more information on these remotes by viewing the top of ``.repo/manifest.xml`` in your initialized BUILDDIR.

Sync
----

Now that you've got your manifest filled out, simply type the following to get all of your source::

    repo sync -c

This will take a while as it will download up to 25GB of sources. If you have a fast computer and connection, you may add an extra ``-j[number]`` flag to make more parallel downloading jobs. We generally recommend ``-j10``, but 6 is the default.


Document
--------

After following these steps, create an issue on the `Halium project management repository <https://github.com/Halium/projectmanagement>`_ to document your manifest and your porting progress.


Next steps
----------

Now that you've got your source tree downloaded, you can move on to the next page where we'll start to build it!
