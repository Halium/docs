
Q. Is my device supported?

A. Not right now, Initially we will prototype the base for the hammerhead device (nexus 5) and once base is stable enough we will add support for more devices.

Q. What about project <insert project name>

A. See blog post [here](http://halium.org/announcements/2017/04/24/halium-is-in-the-air.html)

Q: Why is systemd involved ?

A: Some hardware functionalities (rild, sensors...) are provided by Android services, which must be started at boot time. Therefore an integration in the init system is needed.

Q: The component X is common to all distributions; why not include it in Halium ?

A: Each distribution has its own way of integrating and building its components. Most of the time, the same upstream is already used, so the efforts are already mostly shared. Moreover, Halium wants to address a well identified target, i.e. the hardware abstraction layer using the Android drivers.
