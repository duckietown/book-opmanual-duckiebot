```{seo}
:description: Learn how to perform the intrinsics and extrinsics camera calibration procedure for a Duckietown Duckiebot with step by step instructions.
:keywords: Duckiebot, calibration, camera calibration, intrinsics camera calibration, extrinsics camera calibration
```

```{needget}
- A working Duckiebot: [](ops-db-subsys-testing-intro)
---
- A Duckiebot with a calibrated camera.
```

(db-camera-calibration)=
# Camera Calibration

This chapter describes how to perform the camera calibration procedure for your Duckiebot.

## Introduction to camera calibration

Every camera is unique due to manufacturing and assembly differences. Therefore, a camera calibration procedure needs to be performed to account for small manufacturing discrepancies. 

This procedure involves displaying a predetermined pattern in front of the camera and using it to solve for the camera's parameters.

For more information about the mathematics behind the process, review the appropriate [learning experience](duckiebot-lxs).

<!--
 review [these slides](https://github.com/duckietown/lectures/blob/master/1_ideal/25_computer_vision/cv_calibration.pdf).
-->
(operation-camera-calibration-board)=
## Calibration board

```{figure} ../../_images/calibrations/camera/a3-calibration-pattern.png
:width: 20em
:align: center
:alt: Duckietown camera calibration pattern in A3 format
:name: a3-calibration-pattern

Duckietown camera calibration pattern.
```

If you do not already have a Duckietown calibration board:

1. Download the [Duckietown calibration pattern](https://github.com/duckietown/lib-dt-computer-vision/blob/ente/assets/extrinsics/camera_calibration_pattern_A3_rev0424.pdf)

2. Print it in **A3** format

3. Make sure the printing settings have not deformed the pattern, by measuring the features as indicated on the pattern itself

4. Fix it to a rigid planar surface that you can move around

```{note}
* The squares must have side lengths equal to **0.031 m** (**3.1 cm**). Measure this, as having the wrong size may lead to your Duckiebot crashing.
* In case your squares are not the correct size, make sure that your printer settings are set to **A3** format, with no automatic scaling and size set to `100%`.
```


<!--
`````{tab-set}
````{tab-item} Duckiebot
If you do not already have a Duckietown calibration board:
1. Download the [Duckietown calibration pattern](https://github.com/duckietown/lib-dt-computer-vision/blob/ente/assets/extrinsics/camera_calibration_pattern_A3_rev0424.pdf)
2. Print it in **A3** format
3. Make sure the printing settings have not deformed the pattern, by measuring the features as indicated on the pattern itself
4. Fix it to a rigid planar surface that you can move around

```{note}
* The squares must have side lengths equal to **0.031 m** (**3.1 cm**). Measure this, as having the wrong size may lead to your Duckiebot crashing.
* In case your squares are not the correct size, make sure that your printer settings are set to **A3** format, with no automatic scaling and size set to `100%`.
```
````

````{tab-item} Duckiedrone
If you do not already have a Duckietown calibration board:
1. Download the [Duckietown calibration pattern](https://github.com/duckietown/lib-dt-computer-vision/blob/6d8764c009d4e3d90a08a67af271d89d257d3b17/assets/extrinsics/dd24/camera_calibration_pattern_A4_rev0824.pdf?raw=true)
2. Print it in **A4** format
3. Fix it to a rigid planar surface that you can move around

```{note}
* The squares must have side lengths equal to **0.0175 m** (**1.75 cm**). Measure this, as having the wrong size may lead to your Duckiedrone crashing.
* In case your squares are not the correct size, make sure that your printer settings are set to **A4** format, with no automatic scaling and size set to `100%`.
```
````
`````

-->

```{warning}
If the pattern is not rigid, the calibrations should not be used. You can print on thick paper or adhere to something rigid to achieve this.
```

(operation-camera-intrinsic-calibration)=
## Intrinsic calibration

The instrinsic camera calibration procedure identifies parameters that enable creating a relationship between the 2D image plane and the 3D world around the Duckiebot. These parameters account for various optical specifications such as the camera's focal length, the pixel aspect ratio, and the distortion field applied by the fisheye lens.

For optimal performance, repeat this procedure if you change the focus of the camera by rotating the lens.

### The Intrinsics Calibrator

To perform the intrinsic camera calibration procedure for your Duckiebot, run:

```shell
dts duckiebot calibrate_intrinsics DUCKIEBOT_NAME
```

```{figure} ../../_images/calibrations/camera/intrinsics_calibrator_1.png
:width: 70%
:align: center
:alt: Duckietown instrinsics camera calibration interface
:name: intrinsics_calibrator_1

The Duckietown intrinsics camera calibration interface.
```

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: table:intrinsics-calibrator-commands

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

### Intrinsic calibration procedure

To perform the intrinsic calibration procedure:

1. Move the calibration pattern in front of your Duckiebot's camera such that the **entire** checkerboard pattern is within its field of view and colored lines begin to overlay the checkerboard pattern.
2. Rotate the mechanical focus ring on the lens until you can clearly read the `x` and `y` labels on the checkerboard pattern (do not adjust the focus again or place the lens cover back onto the lens unless you plan on repeating this procedure).
3. Slowly move the calibration board left, right, up, down, forwards and backwards, relative to your Duckiebot's camera, until each region within the `x`, `y` and `Size` bars is filled in.
4. Slowly tilt and pan the calibration board, relative to your Duckiebot's camera, until each region within the `Skew` bar is filled in.
5. Click the `Calibrate` button.
6. Wait for the spinner to disappear.
7. (optional) Click the `Undistort` switch to see an undistorted view of what your Duckiebot sees.

```{figure} ../../_images/calibrations/camera/intrinsics_calibrator_2.png
:width: 70%
:align: center
:alt: Duckietown instrinsics camera calibration interface showing a successful procedure
:name: intrinsics_calibrator_2

The Duckietown intrinsics camera calibration interface (Intrinsics Calibrator) with all of its bars filled in.
```

```{figure} ../../_images/calibrations/camera/intrinsics_calibrator_3.png
:width: 70%
:align: center
:alt: Duckietown instrinsics camera calibration interface showing a successful procedure
:name: intrinsics_calibrator_3

The `Intrinsics Calibrator` with the `Undistort` switch set to `on`.
```

To confirm that a new intrinsic calibration file has been created on your Duckiebot, run the following command and inspect the contents of the `Camera Intrinsic` panel:

```shell
dts duckiebot dashboard DUCKIEBOT_NAME --page robot/calibrations
```

```{figure} ../../_images/calibrations/camera/camera_intrinsic_panel.png
:width: 70%
:align: center
:alt: Duckietown instrinsics camera calibration interface showing a successful procedure
:name: camera_intrinsic_panel

The Camera Intrinsic panel on the Robot page of the Dashboard.
```

```{note}
Within the Camera Intrinsic panel, under `Local`, you should see a tick next to `Completed`, the calibration date next to `Calibration date` and `/data/config/calibrations/camera_intrinsic/DUCKIEBOT_NAME.yaml` next to `Files`.
```

(operation-camera-extrinsic-calibration)=
## Extrinsic camera calibration procedure

This camera calibration procedure outputs the relative pose between the camera and Duckiebot frame. 

For optimal performance, repeat this procedure if you ship the Duckiebot or otherwise touch the camera holder.

### The Extrinsics Calibrator

The easiest way to perform the extrinsic camera calibration procedure for your Duckiebot is by using the `Extrinsics Calibrator`.

```{figure} ../../_images/calibrations/camera/extrinsics_calibrator_1.png
:width: 70%
:align: center
:alt: Duckietown extrinsics camera calibration interface
:name: extrinsics_calibrator_1

The `Extrinsics Calibrator`.
```

To open the `Extrinsics Calibrator`, run:

```shell
dts duckiebot calibrate_extrinsics DUCKIEBOT_NAME
```

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: table:extrinsics-calibrator-commands

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
* - <kbd>E</kbd>
  - Toggle the `Check error` switch
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

### Extrinsic calibration procedure

To perform the extrinsic calibration procedure:

1. (optional) Click the `Check error` switch to enforce a pose error bound for your Duckiebot's camera based on it's known intrinsic parameters (a trapezoid in the image under `Camera View` should appear).
2. Position your Duckiebot on the calibration board such that it faces the checkerboard pattern, your Duckiebot's axle is parallel to and directly above the **large** `y`-axis of the calibration board, and the axis that is perpendicular to and midway between your Duckiebot's axle is directly above the **large** `x`-axis of the calibration board (if the `Check error` switch is set to `on`, the trapezoid in the image under `Camera View` should turn from black to blue).
3. Click the `Calibrate` button.
4. Wait for the spinner to disappear.
5. (optional) Click the `Project` switch to see a top-down view of what your Duckiebot sees under `Projection`.

```{figure} ../../_images/calibrations/camera/extrinsic_setup_db21j_duckiebot.jpg
:width: 70%
:align: center
:alt: Duckiebot extrinsics camera calibration setup
:name: extrinsic_setup


Extrinsic calibration setup: align the Duckiebot with the marks on the calibration pattern, on a white backdrop.
```

```{figure} ../../_images/calibrations/camera/extrinsics_calibrator_2.png
:width: 70%
:align: center
:alt: Duckietown extrinsics camera calibration check error function
:name: extrinsics_calibrator_2

The Extrinsics Calibrator with the Check error switch set to `on`.
```

```{figure} ../../_images/calibrations/camera/extrinsics_calibrator_3.png
:width: 70%
:align: center
:alt: Duckietown extrinsics camera calibration projection functionality
:name: extrinsics_calibrator_3

The Extrinsics Calibrator with the Project switch set to `on`.
```

To confirm that a new extrinsic calibration file has been created on your Duckiebot, run the following command and inspect the contents of the `Camera Extrinsic` panel:

```shell
dts duckiebot dashboard DUCKIEBOT_NAME --page robot/calibrations
```

```{figure} ../../_images/calibrations/camera/camera_extrinsic_panel.png
:width: 70%
:align: center
:alt: Duckietown extrinsics camera calibration extrinsics panel
:name: camera_extrinsic_panel

The `Camera Extrinsic` panel on the `Robot` page of the `Dashboard`.
```

```{note}
Within the `Camera Extrinsic` panel, under `Local`, you should see a tick next to `Completed`, the calibration date next to `Calibration date` and `/data/config/calibrations/camera_extrinsic/DUCKIEBOT_NAME.yaml` next to `Files`.
```

## Troubleshooting

```{trouble}
I do not see what my Duckiebot sees after refreshing the window and following [](db-opmanual-sw-tools-image-viewer).
---
Contact support.
```
