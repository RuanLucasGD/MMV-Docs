
Overview
========

Modules
--------

An **MMV_vehicle** is composed of modules, each module is responsible for controlling some component. An example 
would be an MBT (Main Battle tank) vehicle that contains the modules **MMV_MBT_Engine**, **MMV_MBT_WheelManager**, 
**MMV_TurretController**. The component **MMV_MBT_Vehicle**, the vehicle's main physics script, contains all these 
modules that work together, the data delivered by a given module are used by other modules making them 
interconnected.

Below is a diagram that demonstrates how these modules are wired. The engine must deliver the left and right 
throttle and brake force to the wheel manager, so the wheels will know how much throttle and brake force to apply.
There are specific forces for each side, as each track has its own acceleration and brake, increasing the force 
on one side and decreasing it on the other can cause the vehicle to rotate, thus being a form of steering. How the 
move works will be explained on the next page.

.. figure:: /img/mmv_overview_diagram.png

