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

.. figure:: images/advanced_configurations/vehicle/vehicle_modules.jpg

Let's explain the vehicle component separated by modules.

Engine
------

Module responsible for all parts of the vehicle's power, movement, engine sound and braking system.

Acceleration
............

.. figure:: images/advanced_configurations/vehicle/vehicle_engine_mbt_acceleration.jpg

**max:** The maximum force the vehicle can achieve with acceleration.

**acceleration:** The engine power curve is based on vehicle speed. In this example, when the vehicle is at low speed it has a lot of pulling force and the faster the vehicle will gain speed, but when it reaches maximum speed it will not be able to climb big ravines or push obstacles without losing acceleration and speed.

**slowdown:** Braking force when the vehicle is decelerating, the higher it is, the faster the vehicle will stop when not accelerating.

**forward:** The maximum speed the vehicle can reach moving forward.

**backward:** Maximum speed moving backwards.

**max turn speed:** Maximum speed the vehicle can turn.

**turn acceleration:** Engine acceleration while the vehicle is turning based on speed. Following the example of the image, the slower the vehicle is turning, the greater the acceleration of the engine and the faster the vehicle is turning, the lower the engine force.

Brake
.....

.. figure:: images/advanced_configurations/vehicle/vehicle_engine_mbt_brake.jpg

Maximum vehicle brake force, the higher the faster the vehicle will stop when pressing the brake.

Gears
.....

.. figure:: images/advanced_configurations/vehicle/vehicle_engine_mbt_gears.jpg

Control the number of gears and when to change.

**amount forward/backward:** The amount of gear shifts the vehicle can make


.. note::

    Example of how automatic gear shift times work.

    .. figure:: images/advanced_configurations/vehicle/vehicle_engine_gear_bar_example.svg

**gear (n1 - n2):** The speed at which the vehicle must be to change gears.

Engine Sound
............

.. figure:: images/advanced_configurations/vehicle/vehicle_engine_mbt_engine_sound.jpg

Control the sound of the vehicle's engine.

**audio source:** Any audio source that is in the vehicle that can be used to 
reproduce the sound of the engine.

**audio clip:** Your engine's audio clip.

**min pitch:** The lowest pitch that the engine sound can reach if it's not accelerating.

**max forward/backward pitch:** The maximum pitch that the engine sound can reach when accelerating.

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

.. figure:: images/advanced_configurations/vehicle/vehicle_wheels_mbt.jpg

The wheel module manages all of the vehicle's wheels, applies suspension physics and tells them 
when to accelerate or brake. It makes the vehicle turn and even the tracks move.

Wheels Characteristics
......................

.. figure:: images/advanced_configurations/vehicle/vehicle_wheels_mbt_wheels_characteristics.jpg

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

.. figure:: images/advanced_configurations/vehicle/vehicle_wheels_mbt_tracks.jpg

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

.. figure:: images/advanced_configurations/vehicle/vehicle_mbt_additional_wheels_demo.jpg

Wheels Particles
................

.. figure:: images/advanced_configurations/vehicle/vehicle_wheels_mbt_wheels_particles.jpg

It is possible to add particles to the wheels so that when the vehicle moves, they are installed, such as dust.

.. figure:: images/advanced_configurations/vehicle/vehicle_dust_particle_demo.jpg
.. figure:: images/advanced_configurations/vehicle/vehicle_dust_particle_demo_2.jpg

**left/right particle:** The particle on either side of the vehicle.

**max emission:** The particle on either side of the vehicle.

**stop delay:** The time the particles take to zero from the instant when the vehicle leaves the ground.

Stability
---------

Control vehicle stability.

.. figure:: images/advanced_configurations/vehicle/vehicle_stability.jpg

**Angle deceleration:** how much gravity influences the vehicle when going uphill or steep places.

**center of mass:** The vehicle's center of mass, recommended to leave in the center, the higher on the Y axis, 
the easier it will be for the vehicle to tip over in curves.

Shooter Manager Component
~~~~~~~~~~~~~~~~~~~~~~~~~

Responsible for managing gun fire.

.. figure:: images/advanced_configurations/shooter_manager/shooter_manager.jpg

Shot
----

.. figure:: images/advanced_configurations/shooter_manager/shooter_manager_shot.jpg

Describe all main shooting behavior.

**spawner:** Transform from the position where the shot will come from.

**bullet:** The projectile that will be instantiated. It is important that this object has the Projectile component, read (CREATING PROJECTILE) for more information.

**ignore layer:** The projectile will only identify a collision with another object if it does not have that layer defined.

**bullet velocity:** Speed in meters per second that the projectile moves.

**bullet life time:** After “X” seconds the projectile will be destroyed automatically even without having collided with another object.

**bullet explosion force:** The explosion force that will be assigned to nearby objects when they collide with something.

**bullet explosion range:** The distance to identify nearby objects to apply explosion force after colliding with another object.

**explosion force curve:** The strength of the explosion force over the distance when the projectile collides.

**reload time:** The weapon's reload time.

**recoil:** The force of the shot applied to the vehicle.

Effects
-------

.. figure:: images/advanced_configurations/shooter_manager/shooter_manager_effects.jpg

Applies effects when firing.

**Particles:** Particles that will be instantiated when it fires.

Sound
-----

.. figure:: images/advanced_configurations/shooter_manager/shooter_manager_sound.jpg

**audio source:** Audio source that will be used to play the trigger sound.

**clip:** The audio clip of the shot.

Standart Camera Contoller Component
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Standard MMV camera controller, capable of delivering different types of camera positioning such as 3rd person, 
commander's view and sniper's view.

.. figure:: images/advanced_configurations/camera_controller/standart_camera_controller.jpg

target: add the target vehicle to be followed by the camera.

.. figure:: images/advanced_configurations/camera_controller/standart_camera_controller_inputs.jpg

Add player controls to be able to control the camera, it is possible to configure both keyboard 
and mouse and gamepad.

**See for configure your Axes:** `Unity Input Manager <https://docs.unity3d.com/Manual/class-InputManager.html>`__

**horizontal Axes:** Horizontal Axes of the Input Axes to rotate the camera horizontally.

**vertical Axes:** Vertical Axes of the Input Axes to rotate the camera vertically.

**invert horizontal Axes:** Invert the direction of the player control's horizontal Axes.

**invert vertical Axes:** Invert the direction of the player control's vertical Axes.

**change camera key:** The key or button to switch between cameras if you have more than one.

Camera Behaviour
----------------

.. figure:: images/advanced_configurations/camera_controller/standart_camera_controller_camera_behaviour.jpg

Describe how the camera should behave.

**camera turn speed:** The speed at which the camera rotates

**crosshair layer:** Layer of objects that have a collider.

types
-----

Game cameras.
.............

.. figure:: images/advanced_configurations/camera_controller/standart_camera_controller_types.jpg
    :alt: 0%
    :scale: 80%

.. figure:: images/advanced_configurations/camera_controller/standart_camera_controller_camera_names.jpg

**amount:** Number of vehicle cameras.

Camera "X"
__________

**camera:** The chosen camera.

**type:** The type of camera.

.. note::

    **THIRD_PERSON:** The camera moves around the vehicle and uses the “Camera Collider” to avoid obstacles.

    **FIRST_PERSON:** Stays in the same place, but can be rotated vertically and horizontally.

    .. figure:: images/advanced_configurations/camera_controller/standart_camera_controller_camera_types_demo.jpg

**min vertical:** The minimum angle to the vertical.
**max vertical:** The maximum angle vertically.

Options for FIRST_PERSON
^^^^^^^^^^^^^^^^^^^^^^^^

**max horizontal:** The maximum angle the camera can turn horizontally.

Options for THIRD_PERSON
^^^^^^^^^^^^^^^^^^^^^^^^

**camera height:** The height of the camera relative to the vehicle.

**camera distance:** The distance of the camera from the vehicle

**align to vehicle:** Aligns the Y axis of the camera with that of the vehicle, by default it is already activated in FIRST_PERSON mode.

**camera collision:** Camera collision sensor, prevents it from entering walls, add here the collision layers of your scene, by default the layer is *“Default”*.