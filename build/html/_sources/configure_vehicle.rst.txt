Create your own MMV Main Battle Tank Vehicle
============================================

Before creating your own vehicle, take a look at what comes with the project, 
change some settings so that you understand a little of what each option does, 
but anyway we are trying to make it as simple as possible to configure, alias, 
if by If you find something that doesn't make sense or is difficult to configure 
or understand, please send your feedback to help us make MMV better every day.

Importing vehicle model
~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: img/3d_view_blender_model.png

.. warning::

    Before importing a 3d model, make it follow the defaults of the example vehicle model:

Hierarchy
---------

To create a complete vehicle, you need 8 components, but only 3 are required:
    * Body
    * Turret
    * Cannon
    * Left wheels (all separate)
    * Right wheels (all separate)
    * Armature
    * Left Track (riged)
    * Right Track (riged)

You can follow this example hierarchy to organize your models:

.. figure:: img/mbt_model_hierarchy.png

| **Blue - Empties**
| **Pink - Meshs**
| **Green - Armature**

Orientation
-----------

In order for the MMV to work correctly, make sure your model has **all the 
objects** with the **identity transformation** and must also be pointed with 
the **Z Axis to forward** and and **scale = 1**.

.. warning::
    
    If this is not done, many orientation problems will happen and can 
    generate very annoying bugs, so don't use your model **.Blend** if you 
    use Blender (or any poorly configured model) as the axes may be in the 
    wrong directions.

.. figure:: img/mbt_orientation_incorretly.jpg

.. figure:: img/mbt_orientation_corretly.jpg

Exporting complex models with armor from Blender to Unity with identity 
transformations is a bit complicated, luckily there is a `plugin for Blender 
<https://github.com/EdyJ/blender-to-unity-fbx-exporter>`__ that can do the 
export in a simple way, I recommend you use it to not have so many problems.

.. note::

    If you use other 3D modeling software and also have export issues,  please 
    open a `new Issue <https://github.com/RuanLucasGD/MMV-Docs/issues>`__ so 
    we can work on it.

After installing the plugin, you will have this option along with the other 
export options.

.. figure:: img/export_to_unity_plugin_demonstration.jpg

Tracks
------

.. figure:: img/mbt_tracks_demonstration.png

For treadmill vehicles, there must be 2 models, left treadmill and right 
treadmill that need to be attached to a skeleton. The skeleton must have 
bones that run through the entire mat, one bone per wheel.

.. figure:: img/3d_view_blender_tracks_structure.png

These settings are important because the bones will simulate the movement 
of the conveyor, each bone will follow the position of the wheels (via 
script, no configuration is needed for this in the model), and with this 
the conveyor will follow the position of the wheels .

.. figure:: img/track_movement_demo.gif

Track movement depends on how your UV has been set up. UV influences speed, 
direction and how the belt is drawn on the model.

.. figure:: img/mbt_track_uv.jpg