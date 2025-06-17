```{seo}
:description: How to perform the kinematics calibration procedure for a Duckiebot.
:keywords: Duckietown, Duckiebot, kinematics calibration, odometry
```

(calibration-kinematics)=
# Calibration - Kinematics

This section describes how to perform the kinematics calibration procedure for your Duckiebot.

```{needget}
You can make your Duckiebot move.
---
Your Duckiebot's kinematics will be calibrated.
```

```{attention}
Complete both the **camera** and **kinematics** calibration procedures before running any Duckietown demos.
```

The easiest way to perform the kinematics calibration procedure for your Duckiebot is by using the `Keyboard Controller`.

```{figure} ../../_images/operations/keyboard_controller.png
:name: keyboard-controller

The `Keyboard Controller`.
```

To activate the `Keyboard Controller`, run:

    dts duckiebot keyboard_control ![DUCKIEBOT_NAME]

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: keyboard-controller-commands

* - Key
  - Function
* - <kbd>W</kbd>
  - Drive forwards
* - <kbd>S</kbd>
  - Drive backwards
* - <kbd>A</kbd>
  - Turn left
* - <kbd>D</kbd>
  - Turn right
* - <kbd>E</kbd>
  - Toggle the `Emergency Stop` switch
* - <kbd>F</kbd>
  - Toggle the `Autopilot` switch
* - <kbd>X</kbd>
  - Increase the `Gain`
* - <kbd>Z</kbd>
  - Decrease the `Gain`
* - <kbd>V</kbd>
  - Increase the `Trim`
* - <kbd>C</kbd>
  - Decrease the `Trim`
* - <kbd>Space</kbd>
  - Save the `Gain` and `Trim`
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

## Procedure

To perform the kinematics calibration procedure:
1. Create a slightly greater than `2 m` long straight line on your floor using tape
2. Place your Duckiebot at one end of the line
3. Note your Duckiebot's position
4. Face your Duckiebot towards the other end of the line
5. Drive your Duckiebot forward for about `2 m`
6. Note your Duckiebot's position
7. Measure the distance between the center of the tape and the center of your Duckiebot's axle using a ruler, making sure that the ruler is perpendicular to the tape
8. Decrease (resp., increase) the `Trim` and repeat steps **2**-**8** if your Duckiebot drifted to the left (resp., right) side of the tape by more than `10 cm`
9. Set the `Gain`
10. Click the `Save` button

```{figure} ../../_images/operations/calibration_kinematics/wheel_calibration_line.jpg
:width: 30em
:name: wheel_calibration_line

A straight line used for the kinematics calibration procedure.
```

```{figure} ../../_images/operations/calibration_kinematics/wheel_calibration_lr_drift.jpg
:width: 30em
:name: wheel_calibration_lr_drift

Left/right drift.
```

```{figure} ../../_images/operations/calibration_kinematics/wheel_calibration_measuring_drift.jpg
:width: 30em
:name: wheel_calibration_measuring_drift

Measuring the amount of drift after driving forward for about `2 m`.
```

To confirm that a new kinematics calibration file has been created on your Duckiebot, run the following command and inspect the contents of the `Kinematics` panel:

    dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/calibrations

```{figure} ../../_images/operations/calibration_kinematics/kinematics_panel.png
:name: kinematics_panel

The `Kinematics` panel on the `Robot` page of the `Dashboard`.
```

```{note}
Within the `Kinematics` panel, under `Local`, you should see a tick next to `Completed`, the calibration date next to `Calibration date` and `/data/config/calibrations/kinematics/![DUCKIEBOT_NAME].yaml` next to `Files`.
```

For more information on odometry and odometry calibration, review:
* [video](https://vimeo.com/manage/videos/580764763)
* [theory, activities and exercises](https://github.com/duckietown/mooc-exercises/tree/daffy/modcon).

## Troubleshooting

```{trouble}
My Duckiebot does not move after going through [Operation - Make it Move - Troubleshooting](operation-make-it-move-troubleshooting).
---
Contact support.
```
