
Halium
======

Welcome to the `Halium`_ porting guide. Halium is a collaborative project to unify the Hardware Abstraction Layer for projects which run GNU/Linux on mobile devices with pre-installed Android.

What is porting about - in a nutshell
-------------------------------------
Think of your device as a car. You have got a petrol car (Android). You want to put in an electric driven engine (target OS). In the garage you are told you can put in a diesel engine (e.g. Lineage OS). Fine, so your car is capable of exchanging the engine. Now you need to get all parts for your new engine (kernel, firmware, ...), assemble them and build them into your car (porting). And because every car's chassis is different, you can not use the parts of a Ford to use with a Porsche. That's why every type of car needs its own engine (port). Got it?

Contents
========


.. toctree::
   :maxdepth: 1
   :caption: Porting Guide
   :name: sec-porting

   porting/first-steps
   porting/install_repo
   porting/get-sources
   porting/build-sources
   porting/install-build/index
   porting/debug-build/index

.. toctree::
   :maxdepth: 1
   :caption: Distribution
   :name: sec-distribution

   Distribution

.. toctree::
   :maxdepth: 1
   :caption: Supplementary Information
   :name: sec-supplemental

   supplementary/about-this-chapter
   supplementary/devices/index
   supplementary/hardware-enablement
   supplementary/how-to-document

.. toctree::
   :maxdepth: 1
   :caption: Project
   :name: sec-planning

   project/Scope
   project/Related-projects
   project/Planning
   project/Development
   project/todo

.. _halium: https://halium.org/
