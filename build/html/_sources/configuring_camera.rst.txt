==================
MMV Camera Control
==================

The MMV comes with a standard third-person camera that can be controlled 
with a mouse or gamepad to guide the vehicle's sights.

.. figure:: /img/configuring_camera/camera_movement_demo.gif

Adding Camera
~~~~~~~~~~~~~

To have a camera controller, just have a common camera in your scene and 
add the component ``MMV_CameraController``.

.. figure:: /img/configuring_camera/adding_camera_controller.jpg 
    :scale: 70% 

The camera controller needs a vehicle to track and send the target's position 
to the tower controller. Add your vehicle here:

.. figure:: /img/configuring_camera/camera_controller_target_null.jpg
    :scale: 70%

when added, a series of options will appear so that you can adjust the 
camera as you see fit. 

.. figure:: /img/configuring_camera/camera_controller_component.jpg
    :scale: 70%

If your project inputs are the defaults, this is already capable of making the camera work already.

.. figure:: img/configuring_camera/camera_controller_inputs_1.jpg

.. warning::

    Before starting the game, be sure to move the vehicle to the ``Ignore Raycast`` layer 
    **(or any other layer that is different from the layer used by the crosshairs that 
    will be explained below)**

    .. figure:: img/configuring_camera/vehicle_ignore_layer.jpg

Okay, your camera is now functional!

.. figure:: img/configuring_camera/camera_example.jpg

Advanced Configuration
~~~~~~~~~~~~~~~~~~~~~~

Review of all controller properties

Controll inputs
...............

Use Unity's input settings, configure your Axis or add some new ones to the gamepad

.. figure:: img/configuring_camera/camera_controller_inputs_1.jpg

* **horizontal Axis:** mouse horizontal movement input (Mouse/Gamepad-Joystick X).
* **vertical Axis:** mouse vertical movement input (Mouse/Gamepad-Joystick Y).
* **zoom key:** key to activate the camera's zoom (to apply zoom press the chosen key and move the Mouse/Gamepad-Joystick forwards or backwards).
* **invert horizontal axis:** reverses Mouse/Gamepad horizontal movement speed.
* **invert vertical axis:** reverses Mouse/Gamepad vertical movement speed.

Camera position
...............

Camera location, view control

.. figure:: img/configuring_camera/camera_controller_position.jpg

* **camera height:** the height that the camera will be relative to the vehicle.
* **max vertical angle:** maximum angle of vertical rotation that the camera can be.
* **min vertical angle:** maximum angle of vertical rotation that the camera can be.
* **rotation speed:** camera rotation speed.

Camera zoom
...........

Move the camera closer or farther away from the vehicle

.. figure:: img/configuring_camera/camera_controller_zoom.jpg

* **max camera distance:** the maximum distance the camera can be from the vehicle.
* **min camera distance:** the minimum distance that the camera can be from the vehicle.
* **camera zoom speed:** speed the camera moves forward or backward while zooming.

Camera crosshair
................

Target detection.

.. figure:: img/configuring_camera/camera_controller_crosshair.jpg

* **max crosshair distance:** The maximum distance the camera can see to detect targets.
* **collision layer:** layer where all objects that can serve as obstacles are found (collision objects).

.. warning::

    The layer of **your vehicle (player)** must not be the same as the ``collision layer``.