Custom Controllers
==================

MBT Vehicle
~~~~~~~~~~~

**MMV** allows you to create scripts to control vehicles and their components in a simple way. 
Use this if you want to fit a vehicle into a game with mechanics different from those proposed 
by standard MMV controllers, such as top down or strategy games.

Moving the vehicle to a world position
---------------------------------------

Before starting, you need a vehicle already configured, without the control component, just the 
vehicle itself.

.. figure:: images/custom_controlers/vehicle_default.jpg

Create a script to control our vehicle, it should look like this.

.. code-block:: csharp

    using UnityEngine;
    using MMV;
    
    public class VehicleMoveTo : MonoBehaviour
    {
        public Transform target;
    
        private float deathCurve = 0.1f;        // do not turn to the direction to the target if the angle to it is small.
        private float turnWithAngle = 45.0f;    // when the angle to the target is too big, turn full force to the target.
        private float brakeVelocity = 2.0f;     // if the vehicle is turning at full speed to the right or left, check that the speed is high. If so, brake.
    
        private MMV_MBT_Vehicle vehicle;
    
        void Start() => vehicle = GetComponent<MMV_MBT_Vehicle>();
    
        void Update()
        {
            vehicle.MoveTo(target: target.position, deathCurve: deathCurve, brakeVelocity: brakeVelocity, turnWithAngle: turnWithAngle);
        }
    }

This script is responsible for telling the vehicle where to go, and how to behave in turns.
To tell where to go, simply pass the potion from the target to the vehicle.
The way it behaves is dictated by these 3 variables, **deathCurve**, **turnWithAngle**, **brakeVelocity.**

**deathCurve:** The dead angle to the target, the vehicle will simply not turn if the angle to the 
target is less than deathCurve. Example:

.. figure:: images/custom_controlers/death_curve_example.svg

**turnWithAngle:** tells the vehicle that when it has to make a very big turn to the target it should use all the 
throttle to turn left or right.

.. figure:: images/custom_controlers/turn_with_angle_example.svg

**BrakeVelocity:** Says that if the vehicle needs to turn with full throttle to the left or right, the 
vehicle must stop if it is above the brakeVelocity speed before turning, ensuring that it is more 
agile in the curve.

Script result

.. note::

    The turret is always turning to the same position as the target has not been passed to the turret to aim.

.. figure:: images/custom_controlers/vehicle_move_to_demo.gif

Integration with NavMeshAgent AI
--------------------------------


MMV also supports Unity's navmesh system, allowing us to create more elaborate AIs in a simple way, 
what we need to do is create a **child** `navMeshAgent <https://docs.unity3d.com/Manual/nav-CreateNavMeshAgent.html>`__ 
of the vehicle and pass it to our controller, this is already capable of making the vehicle walk to 
the target using scene `NavMesh <https://docs.unity3d.com/Manual/nav-BuildingNavMesh.html>`__.

.. figure:: images/custom_controlers/vehicle_ai_example.jpg

Let's assume you already have a navmesh set up in the scene.

Use this base script to control your vehicle using NavMesh features:

.. code-block:: csharp

    using UnityEngine;
    using UnityEngine.AI;
    using MMV;
    
    public class VehicleAI : MonoBehaviour
    {
        public Transform target;
    
        private NavMeshAgent agent;
        private MMV_MBT_Vehicle vehicle;
    
        private float deathCurve = 0.1f;        // do not turn to the direction to the target if the angle to it is small.
        private float turnWithAngle = 45.0f;    // when the angle to the target is too big, turn full force to the target.
        private float brakeVelocity = 1f;       // if the vehicle is turning at full speed to the right or left, check that the speed is high. If so, brake.
    
    
        // To follow the path the vehicle needs to make curves, if it is at high speed it will leave the path so add this variable so
        // that the vehicle detects approaching curves so it can decelerate when it gets close.
        private float detectCurveInDistance = 20;
    
        // When the curve is detected and the vehicle decelerates, set a minimum speed so the vehicle does not move too slowly.
        private float minVelocity = 10;
    
        void Start()
        {
            agent = GetComponentInChildren<NavMeshAgent>();
            vehicle = GetComponent<MMV_MBT_Vehicle>();
        }
    
        void Update()
        {
            vehicle.MoveTo(agent: agent, target: target.position, deathCurve: deathCurve, brakeVelocity: brakeVelocity, detectCurveInDistance: detectCurveInDistance, minVelocity: minVelocity);
        }
    }

As you can see, there are two more vehicle control variables in our script:

**detectCurveInDistance:** The distance that the vehicle detects a curve to start decelerating, 
preventing it from going off course in curves if it is at high speed.

.. figure:: images/custom_controlers/detect_curve_distance.svg

**minVelocity:** Assign a minimum speed to the vehicle so that it does not go too slowly in curves.

.. figure:: images/custom_controlers/vehicle_navmesh_ai_demo.gif

Controlling turret rotation
---------------------------

To control the shooting turret's movement, we simply need to tell it where to aim.

Unlike other controllers, aiming is done through a `delegate <https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/using-delegates>`__, 
you write a method that returns the target's position and assigns it the turret.

.. code-block:: csharp

    using UnityEngine;
    using MMV;
    
    public class VehicleTurretController : MonoBehaviour
    {
        public Transform target;
        private MMV_MBT_Vehicle vehicle;
    
        void Start()
        {
            vehicle = GetComponent<MMV_MBT_Vehicle>();
            vehicle.TurretCannonTargetPosition = GetTargetPosition;   // <--- pass as delegate
        }
    
        Vector3 GetTargetPosition()
        {
            return target.position;
        }
    }

.. figure:: images/custom_controlers/turret_moviment_demo.gif

Weapon System
~~~~~~~~~~~~~~

The weapon system comes down to how simple it is to create a custom controller. 
Just access the shot manager script and ask for a shot. Remember that you need to have the fire 
system already configured in your vehicle.

.. figure:: images/custom_controlers/vehicle_shooter_manager.jpg

.. figure:: images/custom_controlers/vehicle_shooter_demo.gif