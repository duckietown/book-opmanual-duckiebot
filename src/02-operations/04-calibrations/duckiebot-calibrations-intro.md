(ops-db-calibrations)=
# Operations - Calibrations

```{seo}
:description: Get you Duckiebot ready to operate autonomously by performing calibrations for its sensors and actuators.
:keywords: duckiebot, camera calibration, motor calibration, robot calibration, odometry, calibration, extrinsics camera calibration, intrinsics camera calibration, duckiebot does not go straight, duckiebot does not work
```

```{needget}
- A working Duckiebot: [](ops-db-subsys-testing-intro)
---
- A calibrated Duckiebot
```

While all Duckiebots might look the same, each one is unique and different from the others due to manufacturing, assembly and sometimes handling differences. 

Performing calibration procedures for the Duckiebot's sensors and actuators is a prerequisite for obtaining smooth autonomous behaviors. In particular:

- the [camera calibration](db-camera-calibration), performed in two steps ([extrinsics](operation-camera-extrinsic-calibration), [intrinsics](operation-camera-intrinsic-calibration)), allows the Duckiebot to (a) create a relation between features in the image plane (2D) to the world around it (3D), and (b) determine the relative positioning of the camera reference frame and the Duckiebots' reference frame.

- the [motor (or wheel) calibration](db-wheels-calibration) allows the robot to go (almost) straight when commanded to do so. In other words, when equal inputs are provided to the left and right motors, this calibration enables the wheel to travel the same distance in a unit time.
