```{seo}
:description: How to perform the camera calibration procedure for a Duckiebot.
:keywords: Duckietown, Duckiebot, camera calibration
```

(calibration-camera)=
# Calibration - Camera

This section describes how to perform the camera calibration procedure for your Duckiebot.

Every camera is unique. Therefore, a camera calibration procedure needs to be performed to account for small manufacturing discrepancies.
This procedure involves displaying a predetermined pattern in front of the camera and using it to solve for the camera's parameters.
For more information, review [these slides](https://github.com/duckietown/lectures/blob/master/1_ideal/25_computer_vision/cv_calibration.pdf).

```{needget}
You can see what your Duckiebot sees.
---
Your Duckiebot's camera will be calibrated.
```

```{attention}
Complete both the **camera** and **kinematics** calibration procedures before running any Duckietown demos.
```

(operation-camera-calibration-board)=
## Calibration board

```{figure} ../../_images/operations/calibration_camera/a3-calibraion-pattern.png
:width: 20em
:name: duckietown-calibration_pattern

Duckietown calibration pattern.
```

`````{tab-set}
````{tab-item} Duckiebot
If you do not already have a Duckietown calibration board:
1. Download the [Duckietown calibration pattern](https://github.com/duckietown/lib-dt-computer-vision/blob/ente/assets/extrinsics/camera_calibration_pattern_A3_rev0424.pdf)
2. Print it in **A3** format
3. Fix it to a rigid planar surface that you can move around

```{note}
* The squares must have side lengths equal to **0.031 m** (**3.1 cm**). Measure this, as having the wrong size may lead to your Duckiebot crashing.
* In case your squares are not the correct size, make sure that your printer settings are set to **A3** format, with no automatic scaling and size set to 100%.
```
````

````{tab-item} Duckiedrone
If you do not already have a Duckietown calibration board:
1. Download the [Duckietown calibration pattern](https://github.com/duckietown/lib-dt-computer-vision/blob/6d8764c009d4e3d90a08a67af271d89d257d3b17/assets/extrinsics/dd24/camera_calibration_pattern_A4_rev0824.pdf?raw=true)
2. Print it in **A4** format
3. Fix it to a rigid planar surface that you can move around

```{note}
* The squares must have side lengths equal to **0.0175 m** (**1.75 cm**). Measure this, as having the wrong size may lead to your Duckiedrone crashing.
* In case your squares are not the correct size, make sure that your printer settings are set to **A4** format, with no automatic scaling and size set to 100%.
```
````
`````

```{warning}
If the pattern is not rigid, the calibrations should not be used. You can print on thick paper or adhere to something rigid to achieve this.
```

(operation-camera-intrinsics-calibration)=
## Intrinsics calibration

### The Intrinsics Calibrator

The easiest way to perform the intrinsics camera calibration prodecure for your Duckiebot is by using the `Intrinsics Calibrator`.

```{figure} ../../_images/operations/calibration_camera/intrinsics_calibrator_1.png
:name: intrinsics-calibrator-1

The `Intrinsics Calibrator`.
```

To activate the `Intrinsics Calibrator`, run:

    dts duckiebot calibrate_intrinsics ![DUCKIEBOT_NAME]

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: intrinsics-calibrator-commands

* - Key
  - Function
* - <kbd>X</kbd>
  - Increase the `Frame Rate`
* - <kbd>Z</kbd>
  - Decrease the `Frame Rate`
* - <kbd>Space</kbd>
  - Calibrate the camera
* - <kbd>F</kbd>
  - Toggle the `Undistort` switch
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

### Procedure

To perform the intrinsics calibration procedure:
1. Move the calibration board in front of your Duckiebot's camera such that the **entire** checkerboard pattern is within its field of view and colored lines begin to overlay the checkerboard pattern
2. Rotate the mechanical focus ring on the lens until you can clearly read the `x` and `y` labels on the checkerboard pattern (do not adjust the focus again or place the lens cover back onto the lens unless you plan on repeating this procedure)
3. Slowly move the calibration board left, right, up, down, forwards and backwards, relative to your Duckiebot's camera, until each region within the `x`, `y` and `Size` bars is filled in
4. Slowly tilt and pan the calibration board, relative to your Duckiebot's camera, until each region within the `Skew` bar is filled in
5. Click the `Calibrate` button
6. Wait for the spinner to disappear
7. (optional) Click the `Undistort` switch to see an undistorted view of what your Duckiebot sees

```{figure} ../../_images/operations/calibration_camera/intrinsics_calibrator_2.png
:name: intrinsics-calibrator-2

The `Intrinsics Calibrator` with all of its bars filled in.
```

```{figure} ../../_images/operations/calibration_camera/intrinsics_calibrator_3.png
:name: intrinsics-calibrator-3

The `Intrinsics Calibrator` with the `Undistort` switch set to `on`.
```

To confirm that a new intrinsics calibration file has been created on your Duckiebot, run the following command and inspect the contents of the `Camera Intrinsic` panel:

    dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/calibrations

```{figure} ../../_images/operations/calibration_camera/camera_intrinsic_panel.png
:name: camera-intrinsic-panel

The `Camera Intrinsic` panel on the `Robot` page of the `Dashboard`.
```

```{note}
Within the `Camera Intrinsic` panel, under `Local`, you should see a tick next to `Completed`, the calibration date next to `Calibration date` and `/data/config/calibrations/camera_intrinsic/![DUCKIEBOT_NAME].yaml` next to `Files`.
```

(operation-camera-extrinsics-calibration)=
## Extrinsics calibration

### The Extrinsics Calibrator

The easiest way to perform the extrinsics camera calibration procedure for your Duckiebot is by using the `Extrinsics Calibrator`.

```{figure} ../../_images/operations/calibration_camera/extrinsics_calibrator_1.png
:name: extrinsics-calibrator-1

The `Extrinsics Calibrator`.
```

To activate the `Extrinsics Calibrator`, run:

    dts duckiebot calibrate_extrinsics ![DUCKIEBOT_NAME]

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: extrinsics-calibrator-commands

* - Key
  - Function
* - <kbd>X</kbd>
  - Increase the `Frame Rate`
* - <kbd>Z</kbd>
  - Decrease the `Frame Rate`
* - <kbd>Space</kbd>
  - Calibrate the camera
* - <kbd>F</kbd>
  - Toggle the `Project` switch
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

### Procedure

To perform the extrinsics calibration procedure:
1. Position your Duckiebot on the calibration board such that it faces the checkerboard pattern, your Duckiebot's axle is parallel to and directly above the **large** `y`-axis of the calibration board, and the axis that is perpendicular to and midway between your Duckiebot's axle is directly above the **large** `x`-axis of the calibration board (the trapezoid in the image under `Camera View` should turn from black to green)
2. Click the `Calibrate` button
3. Wait for the spinner to disappear
4. (optional) Click the `Project` switch to see a top-down view of what your Duckiebot sees under `Projection`

```{figure} ../../_images/operations/calibration_camera/extrinsic_setup.jpg
:width: 30em
:name: extrinsics-calibration-setup

Extrinsics calibration setup.
```

```{figure} ../../_images/operations/calibration_camera/extrinsics_calibrator_2.png
:name: extrinsics-calibrator-2

The `Extrinsics Calibrator` with the `Project` switch set to `on`.
```

To confirm that a new extrinsics calibration file has been created on your Duckiebot, run the following command and inspect the contents of the `Camera Extrinsic` panel:

    dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/calibrations

```{figure} ../../_images/operations/calibration_camera/camera_extrinsic_panel.png
:name: camera-extrinsic-panel

The `Camera Extrinsic` panel on the `Robot` page of the `Dashboard`.
```

```{note}
Within the `Camera Extrinsic` panel, under `Local`, you should see a tick next to `Completed`, the calibration date next to `Calibration date` and `/data/config/calibrations/camera_extrinsic/![DUCKIEBOT_NAME].yaml` next to `Files`.
```

## Troubleshooting

```{trouble}
I do not see what my Duckiebot sees after refreshing the window and going through [Operation - Make it See - Troubleshooting](operation-make-it-see-troubleshooting).
---
Contact support.
```
