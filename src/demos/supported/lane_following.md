(demo-lane-following)=
# Lane following (`LF`)

```{needget}
* An assembled and initialized Duckiebot;
* [Wheels calibration](#wheel-calibration) completed;
* [Camera calibration](#camera-calib) completed;
* [Joystick demo](#rc-control) has been successfully launched;
* A Duckietown city loop, as detailed in the [appearance specifications](book-opmanual-duckietown:book).
---
* A Duckiebot driving autonomously in a Duckietown city loop, without other vehicles, intersections, or obstacles.
```

(demo-lane-following-expected)=
## Expected results

```{admonition} Outcome of the lane following demo.
<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/334931570" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
<p><a href="https://vimeo.com/334931570">A Duckiebot following the lane.</a> from <a href="https://vimeo.com/duckietown">Duckietown</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
```

```{todo}
Fix video above, it does not use the proper vimeo directive.
```


(demo-lane-following-duckietown-setup)=
## Duckietown setup notes

Before getting started, make sure your Duckietown is ready to go:
- The layout adheres to the [](book-opmanual-duckietown:book);
- The lighting is "good": ideally white diffused light. This demo relies on images from the camera and 
  color detections, so avoid colored lights, reflections or other conditions that might confuse or blind 
  the onboard image sensor;


(demo-lane-following-duckiebot-setup)=
## Duckiebot setup notes

* Duckiebot in configuration [DB21M, DB21J, or DB19](duckiebot-configurations). 
* The Duckiebot is powered on and connected to your network. You should be able to successfully ping it from your base station;
* You are able to [see what the Duckiebot sees](make-it-see);
* You are able to [remote control](rc-control) your Duckiebot; 
* The [camera is calibrated](camera-calib);
* The [wheels are calibrated](wheel-calibration).

(demo-lane-following-pre-flight)=
## Pre-flight checklist

* Place the Duckiebot inside a lane (driving on the right-hand side of the road), making sure it sees the lane lines;
* Make sure no containers are running on the Duckiebot which use either the camera or the joystick. We will run these ROS nodes in a new container.

(demo-lane-following-run)=
## Demo instructions

(demo-lane-following-run-demo)=
### Start the lane following demo

To start the lane following (`LF`) demo:

```none
dts duckiebot demo --demo_name lane_following --duckiebot_name ![DUCKIEBOT_NAME] --package_name duckietown_demos
```

It will take a minute for the demo to launch. You can check Portainer if all the containers started successfully, and their logs if any issues arise.

(demo-lane-following-drive)=
### Start driving autonomously

Run the keyboard controller (not necessary if you have a joystick set up instead) and press the indicated key to initialize the driving behavior:

```none
dts duckiebot keyboard_control ![DUCKIEBOT_NAME]
```

```{list-table} Lane following demo start and stop commands
:header-rows: 1
:name: lf-start-commands

* - Controls
  - Joystick
  - Keyboard
* - Start Lane Following
  - __R1__
  - <kbd>a</kbd>
* - Stop Lane Following
  - __L1__
  - <kbd>s</kbd>
```


In case intersections and/or red lines are present in the city layout, they will be neglected. The Duckiebot will drive across them like it is a normal lane. 

You can regain control of the Duckiebot at any moment by stopping the demo using the (virtual) joystick. The demo can be resumed by pressing the start button.

(demo-lane-following-visualization)=
### Visualize the detected line segments

This step is optional, and it provides a visualization of the line segments that the Duckiebot detects, and is useful to debug eventual weird behaviors. 

* Make the `lane_filter_node` publish all the image topics. The `start_gui_tools` will provide a shell that is connected to the ROS agent:

```none
dts start_gui_tools ![DUCKIEBOT_NAME]
```

* Run `rqt_image_view` and select the `/ROBOT_NAME/line_detector_node/debug/segments/compressed`. You should see something like this:

    ```{admonition} Outcome of the line detector node.
    <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/334931437" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
    <p><a href="https://vimeo.com/334931437">Line segment detections</a> from <a href="https://vimeo.com/duckietown">Duckietown</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
    ```

* In `rqt_image_view` by selecting the `/ROBOT_NAME/ground_projection_node/debug/ground_projection_image/compressed` you should see a top-down view of the detected segments:

    ```{figure} ../../_images/demos/lane_following/ground_projection_segments.png
    :width: 30em
    :name: fig:ground_projection_lf

    Line segments projected on the ground
    ```

(demo-lane-following-troubleshooting)=
## Troubleshooting 

```{trouble}
The demo does not respond why pressing the start or stop buttons
---
Make sure the keyboard controller window is actively selected
```

```{trouble}
The Duckiebot does not move
---
* Check if you can manually drive the Duckiebot
  * Try re-launching `dts duckiebot keyboard_control ![hostname]`
* Check if ROS messages are received on the robot on the `![hostname]/joy` topic
```

```{trouble}
The Duckiebot does not stay in the lane, or overall exhibits a bad driving behavior
---
This can be due to a number of issues, e.g.: bad robot calibrations, bad perception of lines due to inappropriate lighting or non-respected appearance specifications of the town, and/or bad tunining of the lane PID controller. The best way to debug this is to:  

* Check `rqt_image_view` and look at `image_with_lines`.
  * Check if you see enough segments. If not enough segments are visible, reset the Anti-Instagram filter.
  * Check if you see more segments and the color of the segments are according to the color of the lines in Duckietown
* Check your camera [calibrations](#camera-calib) are good.
```

```{trouble}
The Duckiebot does not drive nicely through intersections
---
For this demo, there should not be any intersections in the city layout. Duckiebots will interpret intersections as "broken" lanes, perceiving less salient features, potentially compromising the state estimate hence causing the driving troubles.
```

```{trouble}
The Duckiebot does not drive nicely through intersections
---
For this demo, there should not be any intersections in the city layout. Duckiebots will interpret intersections as "broken" lanes, perceiving less salient features, potentially compromising the state estimate hence causing the driving troubles.
```

````{trouble}
The Duckiebot cuts white line while driving on inner curves (advanced)
---
This might be due to wrongly constructed lanes or bad Duckiebot calibrations. Fortunately, feedback control should take care of most of these problems.  

While running the demo modify the PID controller gains from the base station through:

```bash
rosparam set /![DUCKIEBOT_NAME]/lane_controller_node/k_d -45
rosparam set /![DUCKIEBOT_NAME]/lane_controller_node/k_theta -11
```

````
