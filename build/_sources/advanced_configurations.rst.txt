.. _advanced-configurations:

Advanced Components Configuration
=================================

Welcome to the **MMV** advanced settings module. Here will be shown each property of each official 
component of the system. In the previous modules, a view was made above each component in order 
to show how the system works in general, but when we want something more complete it is important 
to know about all the possibilities of asset configurations.

Vehicle Component
~~~~~~~~~~~~~~~~~

A vehicle component is composed of some modules, each module controls a specific part as you can 
see in the image.

.. figure:: images/advanced_configurations/vehicle_modules.png

Let's explain the vehicle component separated by modules.

Engine
------

Module responsible for all parts of the vehicle's power, movement, engine sound and braking system.

Acceleration
............

.. figure:: images/advanced_configurations/vehicle_engine_mbt_acceleration.png

**max:** The maximum force the vehicle can achieve with acceleration.

**acceleration:** The engine power curve is based on vehicle speed. In this example, when the vehicle is at low speed it has a lot of pulling force and the faster the vehicle will gain speed, but when it reaches maximum speed it will not be able to climb big ravines or push obstacles without losing acceleration and speed.

**slowdown:** Braking force when the vehicle is decelerating, the higher it is, the faster the vehicle will stop when not accelerating.

**forward:** The maximum speed the vehicle can reach moving forward.

**backward:** Maximum speed moving backwards.

**max turn speed:** Maximum speed the vehicle can turn.

**turn acceleration:** Engine acceleration while the vehicle is turning based on speed. Following the example of the image, the slower the vehicle is turning, the greater the acceleration of the engine and the faster the vehicle is turning, the lower the engine force.

Brake
.....

.. figure:: images/advanced_configurations/vehicle_engine_mbt_brake.png

Maximum vehicle brake force, the higher the faster the vehicle will stop when pressing the brake.

Gears
.....

.. figure:: images/advanced_configurations/vehicle_engine_mbt_gears.png

Control the number of gears and when to change.

**amount forward/backward:** The amount of gear shifts the vehicle can make


.. note::

    Example of how automatic gear shift times work.

    .. figure:: images/advanced_configurations/vehicle_engine_gear_bar_example.svg

**gear (n1 - n2):** The speed at which the vehicle must be to change gears.

Engine Sound
............

.. figure:: images/advanced_configurations/vehicle_engine_mbt_engine_sound.png

Control the sound of the vehicle's engine.

**audio source:** Any audio source that is in the vehicle that can be used to 
reproduce the sound of the engine.

**audio clip:** Your engine's audio clip.

**min pitch:** The lowest pitch that the engine sound can reach if it's not accelerating.

**max forward/backward pitch:** The maximum pitch that the engine sound can reach when accelerating.

Turret
------

.. figure:: images/advanced_configurations/vehicle_turret.png

This module is responsible for controlling the turret and aiming the vehicle.

Transforms
..........

.. figure:: images/advanced_configurations/vehicle_turret_demo.png

**turret:** Vehicle weapon system turret.

**cannon:** Cannon that is connected to the vehicle's turret.

**horizontal velocity:** The speed at which the turret flips horizontally towards the target.
**vertical velocity:** The speed at which the cannon turns vertically towards the target.

Wheels
------

.. figure:: images/advanced_configurations/vehicle_wheels_mbt.png

The wheel module manages all of the vehicle's wheels, applies suspension physics and tells them 
when to accelerate or brake. It makes the vehicle turn and even the tracks move.

Wheels Characteristics
......................

.. figure:: images/advanced_configurations/vehicle_wheels_mbt_wheels_characteristics.png

Demo of wheel gizmos:


**radius:** The size of each wheel.

Spring
______

**length:** The length of the suspension, the longer the higher the vehicle will be.

**height:** Used as a suspension start marker, this property does not impact the appearance 
of the vehicle's suspension, but when properly configured it prevents physics errors. The 
ideal is to leave the height within or at least a little above the wheel position, so that 
when the suspension is 100% compressed there are no miscalculations.

**stiffness:** Resistance of the suspension, the higher, the stiffer the suspension of the vehicle.

**damper:** Smoothing, softens the force of the suspension when it is compressed, preventing the vehicle 
from “bouncing” when hitting the ground with force or going over an obstacle.

Friction
________

**forward:** How much the wheels will slide when moving forward or backward.

**side:** How far do the wheels slide to the side.

**multiply:** Multiplies forward and side to obtain different skidding behavior, can be used to make the 
vehicle slip when on certain terrain.

Tracks
------

.. figure:: images/advanced_configurations/vehicle_wheels_mbt_tracks.png

Add here the meshes of your vehicle's tracks, so that they follow the movement of the wheels.

**multiply rotation velocity:** If your belt is not moving at the correct speed, change this value 
to correct the speed.

Left/Right Wheels
.................

Add your vehicle's wheels here, if you are in doubt about which objects to place here, see :ref:`adding_physics_on_vehicle`.

**Collider:** Transform of the central position of the wheel (empty object), will be used to calculate the 
suspension and movement of the wheel.

**Mesh:** Another transform that is in the same position as the wheel, but has a MeshRenderer to be the 3D 
model of the wheel.

**Bone:** A track bone, which is next to the wheel.

Left/Right Additional Wheels Renderers
......................................

Add here the wheel meshes that don't apply physics but must rotate along with the others like the front 
and back wheels of the tank.

.. figure:: images/advanced_configurations/vehicle_mbt_additional_wheels_demo.png

Wheels Particles
................

.. figure:: images/advanced_configurations/vehicle_wheels_mbt_wheels_particles.png

It is possible to add particles to the wheels so that when the vehicle moves, they are installed, such as dust.

.. figure:: images/advanced_configurations/vehicle_dust_particle_demo.png
.. figure:: images/advanced_configurations/vehicle_dust_particle_demo_2.png

**left/right particle:** The particle on either side of the vehicle

**max emission:** The particle on either side of the vehicle.

**stop delay:** The time the particles take to zero from the instant when the vehicle leaves the ground.

Stability
---------

Control vehicle stability.

.. figure:: images/advanced_configurations/vehicle_stability.png

**Angle deceleration:** how much gravity influences the vehicle when going uphill or steep places.

**center of mass:** The vehicle's center of mass, recommended to leave in the center, the higher on the Y axis, the easier it will be for the vehicle to tip over in curves.