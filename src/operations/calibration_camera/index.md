(camera-calib)=
# Calibration - Camera

This section describes the intrinsic and extrinsic calibration procedures.

```{needget}
You can see the camera image on the laptop.
---
Your camera intrinsics and extrinsics are calibrated and stored on the Duckiebot. You will be able to access these calibrations via the dashboard.
```

(camera-calibration-pattern-materials)=
## 0) Required  Materials

### Calibration board

```{figure} ../../_images/duckiebot_assembly_and_setup/calibration_camera/a3-calibraion-pattern.png
:width: 20em
:name: fig:calibration_checkerboard

Calibration checkerboard
```

If you do not have one already:

* Download the [Calibration checkerboard pdf](https://github.com/duckietown/duckietown-mplan/blob/a025c99e218687685d80bd72a7f90996572a55c7/hardware/camera_calibration_pattern_A3.pdf)
* Print it with ***A3 Format***
* Fix the checkerboard to a rigid planar surface that you can move around


```{note}
* The squares must have side equal to 0.031 m = 3.1 cm. Please measure this, as having the wrong size will make your Duckiebot crash.
* In case your squares are not of the right size, make sure your printer settings are on A3 format, no automatic scaling, 100% size.
```

```{warning}
If the pattern is not rigid the calibration will be useless. You can print on thick paper or adhere to something rigid to achieve this.
```


### Optional material

This is not necessary, but you could also use a "lane" during the extrinsic calibration procedure.


## 1) Intrinsic Calibration

Every camera is a little bit different, so we need to do a camera calibration procedure to account for the small manufacturing discrepancies.
This process will involve displaying a predetermined pattern to the camera, and using it to solve for the camera parameters.
For more information, see [our theory slides](https://github.com/duckietown/lectures/blob/master/1_ideal/25_computer_vision/cv_calibration.pdf).
And the procedure is basically a wrapper around the [ROS camera calibration tool](http://wiki.ros.org/camera_calibration).

### Launch the intrinsic calibration application

You can launch the intrinsic calibration program with:

```
dts duckiebot calibrate_intrinsics [your_duckiebot_hostname]
```

You should see an application launching, similar to the following figure, on the laptop.

```{figure} ../../_images/duckiebot_assembly_and_setup/calibration_camera/intrinsic_calibration_pre.png
:width: 30em
:name: fig:intrinsic_callibration_pre

Intrinsic camera calibration tool
```

```{trouble}
Only a black window starts up
---
Try resizing the window manually once using cursor, and you should see the window content correctly.
```

### Do the calibration dance

Position the checkerboard in front of the camera until you see colored lines overlaying the checkerboard.
You will only see the colored lines if the **entire** checkerboard is within the field of view of the camera.

Make sure to focus the image by rotating the mechanical focus ring on the lens of the camera until you can clearly read the x and y labels.

```{warning}
Do not adjust the focus again after this process, as it will invalidate the calibration.
```


You should also see colored bars in the sidebar of the display window.
These bars indicate the current range of the checkerboard in the camera's field of view:

- X bar: the observed horizontal range (left - right)
- Y bar: the observed vertical range (top - bottom)
- Size bar: the observed range in the checkerboard size (forward - backward from the camera direction)
- Skew bar: the relative tilt between the checkerboard and the camera direction

Now move the checkerboard right/left, up/down, and tilt the checkerboard
through various angles of relative to the image plane. After each movement,
make sure to pause long enough for the checkerboard to become highlighted. 

The indicator bars will fill as you collect enough data along each axis.

Once you have collected enough data, all four indicator bars will turn green. Then press
the "CALIBRATE" button in the sidebar.

```{tip}
If you are having a difficult time getting the indicator bars to turn green, try slowly increading the extremes at which you present the checkerboard to the camera for each range - focusing on one indicator bar at a time. (Move further left/right along the x axis only, then the y axis, etc.)
```

Calibration may take a few moments. Note that the screen may dim. Don't worry, the calibration is working.


```{figure} ../../_images/duckiebot_assembly_and_setup/calibration_camera/intrinsic_calibration_calibratestep.png
:width: 30em
:name: fig:intrinsic_calibration_calibratestep

Calibration step
```


### Save the calibration results

If you are satisfied with the calibration, you can save the results by pressing the "COMMIT" button in the side bar. (You never need to click the "SAVE" button.)

```{figure} ../../_images/duckiebot_assembly_and_setup/calibration_camera/intrinsic_calibration_commit.png
:width: 30em
:name: fig:intrinsic_calibration_commit

Committing the calibration
```

This will automatically save the calibration results on your Duckiebot:

```
/data/config/calibrations/camera_intrinsic/[your_duckiebot_hostname].yaml
```

You can view or download the calibration file using the Dashboard running at `http://[your_duckiebot_hostname].local` under `File Manager` in the sidebar on the left, navigating to `config/calibrations/camera_intrinsic/`.


### Keeping your calibration valid

```{warning}
* Do not change the focus during or after the calibration, otherwise your calibration is no longer valid.
* Do not use the lens cover anymore; removing the lens cover may change the focus.
```

(extrinsic-camera-calibration)=
## 2) Extrinsic Camera Calibration

(camera-calib-jan18-extrinsics-setup)=
### Setup

Arrange the Duckiebot and checkerboard according to {numref}`fig:extrinsic_setup2`. Note that the axis of the wheels should be aligned with the y-axis.

```{figure} ../../_images/duckiebot_assembly_and_setup/calibration_camera/extrinsic_setup.jpg
:width: 30em
:name: fig:extrinsic_setup2

Extrinsic calibration setup
```

{numref}`fig:extrinsic_view2` shows a view of the calibration checkerboard from the Duckiebot. To ensure proper calibration there should be no clutter in the background.

```{figure} ../../_images/duckiebot_assembly_and_setup/calibration_camera/extrinsic_view.jpg
:width: 30em
:name: fig:extrinsic_view2

Extrinsic calibration view
```


### Launch the extrinsic calibration pipeline

Run:

```
dts duckiebot calibrate_extrinsics [your_duckiebot_hostname]
```

First the output will instruct you place your robot on the calibration box and press <kbd>Enter</kbd>.
If all goes well the program will complete.

And this will automatically save the calibration results on your Duckiebot:

```
/data/config/calibrations/camera_extrinsic/[your_duckiebot_hostname].yaml
```

Similar to intrinsic calibration, you can also view or download the calibration file using the Dashboard.

```{attention}
If you do not see a saved extrinsic calibration file, your Duckiebot was not able detect the calibration checkerboard and generate a valid calibration.

This could be due to
* lack of evenly bright overhead lighting
* A patterned background in the environment
* A textured background wall or the shadowson the background wall

Try changing the calibration environment to match {numref}`extrinsic_view2`.
```

### Confirm the calibration

Use the Dashboard to confirm that both calibration the intrinsic and extrinsic files have been saved.

#### Troubleshooting

```{trouble}
You see a long complicated error message that ends with something about `findChessBoardCorners failed`.
---
Your camera is not viewing the full checkerboard pattern. Most likely part of the chess board pattern is occluded. Possibly you didn't assemble your Duckiebot correctly or you did not put it on the calibration pattern properly.
```
