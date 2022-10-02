.. _wheeled-vehicles:

Tracked vehicle Component Configuration
=======================================

Responsible for simulating the entire system of a vehicle with tracks.

Vehicle Component
~~~~~~~~~~~~~~~~~

A vehicle component is composed of some modules, each module controls a specific part as you can 
see in the image.

.. figure:: images/tracked_vehicle/vehicle_modules.jpg

Let's explain the vehicle component separated by modules.

Engine
------

Module responsible for all parts of the vehicle's power, movement, engine sound and braking system.

.. figure:: images/tracked_vehicle/engine_acceleration.jpg

**Engine Settings:** :ref:`configuration file <engine settings>` containing all engine parameters

Engine Sound
............

.. figure:: images/tracked_vehicle/engine_sound.jpg

Control the sound of the vehicle's engine.

**audio source:** Any audio source that is in the vehicle that can be used to 
reproduce the sound of the engine.

**audio clip:** Your engine's audio clip.

**min pitch:** The lowest pitch that the engine sound can reach if it's not accelerating.

**max pitch:** The maximum pitch that the engine sound can reach when accelerating.

Turret
------

.. figure:: images/advanced_configurations/vehicle/vehicle_turret.jpg

This module is responsible for controlling the turret and aiming the vehicle.

Transforms
..........

.. figure:: images/advanced_configurations/vehicle/vehicle_turret_demo.jpg

**turret:** Vehicle weapon system turret.

**cannon:** Cannon that is connected to the vehicle's turret.

**horizontal velocity:** The speed at which the turret flips horizontally towards the target.
**vertical velocity:** The speed at which the cannon turns vertically towards the target.

Wheels
------

.. figure:: images/tracked_vehicle/wheels.jpg

The wheel module manages all of the vehicle's wheels, applies suspension physics and tells them 
when to accelerate or brake. It makes the vehicle turn and even the tracks move.


**settings:** :ref:`Configuration file <wheel settings>` that contains all the parameters for suspension and behavior of the vehicle's wheels

Tracks
------

.. figure:: images/advanced_configurations/vehicle/vehicle_wheels_mbt_tracks.jpg

Add here the meshes of your vehicle's tracks, so that they follow the movement of the wheels.

**multiply rotation velocity:** If your belt is not moving at the correct speed, change this value 
to correct the speed.

Left/Right Wheels
.................

Add your vehicle's wheels here.

.. figure:: images/tracked_vehicle/wheels_wheels.jpg

**Mesh:** Object that will be used to apply wheel physics on the vehicle.

**Bone:** A track bone, which is next to the wheel.

Left/Right Additional Wheels Renderers
......................................

Add here the wheel meshes that don't apply physics but must rotate along with the others like the front 
and back wheels of the tank.

.. figure:: images/advanced_configurations/vehicle/vehicle_mbt_additional_wheels_demo.jpg

.. figure:: images/tracked_vehicle/wheels_additional_wheels.jpg

Wheels Particles
................

.. figure:: images/tracked_vehicle/wheels_particles.jpg

It is possible to add particles to the wheels so that when the vehicle moves, they are installed, such as dust.

.. figure:: images/advanced_configurations/vehicle/vehicle_dust_particle_demo.jpg
.. figure:: images/advanced_configurations/vehicle/vehicle_dust_particle_demo_2.jpg

**left/right particle:** The particle on either side of the vehicle.

**max emission:** The particle on either side of the vehicle.

Stability
---------

Control vehicle stability.

.. figure:: images/advanced_configurations/vehicle/vehicle_stability.jpg

**Angle deceleration:** how much gravity influences the vehicle when going uphill or steep places.

**center of mass:** The vehicle's center of mass, recommended to leave in the center, the higher on the Y axis, 
the easier it will be for the vehicle to tip over in curves.

