```{seo}
:description: Duckietown lane following autonomous behavior demo. 
:keywords: duckietown, demo, autonomous driving, demonstration, duckiebot, db21, db21-j4, AV, autonomous vehicle, self-driving car, self-driving, robot autonomy, AI robotics
```

(demo-lane-following)=
# Lane following (`LF`)

```{needget}
* An assembled and initialized Duckiebot;
* [Wheels calibration](wheel-calibration) completed;
* [Camera calibration](camera-calib) completed;
* [Joystick demo](rc-control) has been successfully launched;
* A Duckietown city loop, as detailed in the [appearance specifications](book-opmanual-duckietown:book).
OR
* A virtual duckiebot
---
* A Duckiebot driving autonomously in a Duckietown city loop, without other vehicles, intersections, or obstacles.
```

```{admonition} Difficulty Level
Easy
```

(demo-lane-following-expected)=
## Expected results


````{admonition} Newer DB21 Duckiebots following the lane

```{vimeo} 1026496889
:alt: Newer DB21J Duckiebots autonomously driving down the lane with the Duckietown lane following behavior. 

````

````{admonition} An older DB18 Duckiebot following the lane

```{vimeo} 334931570
:alt: An older DB18 Duckiebot following the lane. 

````

```todo
Add video in Duckiematrix?
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

### Clone the `dt-core` Repository

First clone the `dt-core` repository. From the command line run:

```bash
git clone git@github.com:duckietown/dt-core.git -b ente
```

which will create a folder called `dt-core` with the contents of this repository. 
Enter that repository:

```bash
cd dt-core
```

### Optional: Running in the Duckiematrix

If you would like to run the demo in the [Duckiematrix](book-devmanual-duckiematrix:book),
you should start by creating and starting your virtual robot:

```bash
dts duckiebot virtual create ![VIRTUAL_ROBOT_NAME]
dts duckiebot virtual start ![VIRTUAL_ROBOT_NAME]
```

Next, start the duckiematrix with command:

```bash
dts matrix run --standalone -m assets/duckiematrix/maps/loop
```

Then, in another terminal tab, you will need to attach your virtual robot
to the entity in the duckiematrix by running:

```bash
dts matrix attach ![VIRTUAL_ROBOT_NAME] map_0/vehicle_0
```

```testexpect
Open a virtual joystick with

    dts duckiebot keyboard_control ![VIRTUAL_ROBOT_NAME]

---
Pushing the controls on the virtual joystick should cause your robot
to move in the duckiematrix.
```

### Build and Run the code

Next build the code on your robot. From the `dt-core` directory run:

```bash
dts devel build -H ![ROBOTNAME]
```

where `![ROBOTNAME]` is the name of your robot (virtual or real).

and then run with:

```bash
dts devel run -H ![ROBOTNAME] -L lane-following
```

When the demo is ready, you should see the LEDs on the Duckiebot turn <green>GREEN</green>

(demo-lane-following-drive)=
### Start Autonomous Lane Following

Run the keyboard controller:
 
```none
dts duckiebot keyboard_control ![DUCKIEBOT_NAME]
```
and press <kbd>A</kbd>
to start the lane following "Autopilot". You should see the front LEDs on the Duckiebot turn white 
and the back ones turn <red>RED</red>. The Duckiebot should start to follow the lane. 

You can stop the "Autopilot" and return to joystick control by pressing <kbd>S</kbd>.

In case intersections and/or red lines are present in the city layout, they will be neglected. 
The Duckiebot will drive across them like it is a normal lane. 

If things are not working as expected, please look at the [](demo-lane-following-parameter-tuning) or 
[](demo-lane-following-troubleshooting) sections for suggestions.

(demo-lane-following-visualization)=
### Visualizations

It can be interesting and informative to look at some of the intermediate signals.


This step is optional, and it provides a visualization of the line segments that the Duckiebot detects, and is useful to debug eventual weird behaviors. 


```none
dts gui ![DUCKIEBOT_NAME]
```

This gives you access to a terminal where you can use all of the ROS utilities. For example, 
you can see all of the ROS topics that are available by running

```bash
rostopic list
```

For a more exhaustive list of these tools, see [](ops-tools).

* Run `rqt_image_view` and select the 
`/ROBOT_NAME/line_detector_node/debug/segments/compressed` topic in the dropdown.
 ou should see something like this:

    ````{admonition} Outcome of the line detector node

    ```{vimeo} 334931437
    :alt: Line segment detections from Duckiebots in Duckietown. 

    ````

* In `rqt_image_view` by selecting the 
`/ROBOT_NAME/ground_projection_node/debug/ground_projection_image/compressed` in the dropbown
you should see a top-down view of the detected segments:

    ```{figure} ../../_images/demos/lane_following/ground_projection_segments.png
    :width: 30em
    :name: fig:ground_projection_lf

    Line segments projected on the ground
    ```
```{todo}
update
```
(demo-lane-following-how-it-works)=
## How it Works

While our objective here will not be to explain in intricate detail how the entire demo is working 
(this is covered in more detail in the Learning Experiences), it can be useful to understand
the gist of how things are working to help with debugging potential problems. 

```{todo}
Add a better figure of the overview of the processing pipeline
```
```figure ../../_images/demos/lane_following/processing_flow.png
    :width: 30em
    :name: Lane Detection Process 

 Full lane following processing flow, from input image to belief

```


At a high level, the following processing steps are being applied:

 1. **Image Capture**: The image is being read from the camera and published to ROS. You can view the camera output through the `![ROBOTNAME]/camera_node/image/compressed` topic in `rqt_image_view`.
 2. **Line Detection**: Next the colored lines in the image are detected.
 3. **Ground Projection**: Based on the known camera extrinsic and intrinsic parameters, we can project the lines that we detected in the image onto the ground (road) plane.
 4. **Lane Estimation**: All of the ground projected line segments, together with the motion of the robot which we can estimate with help from the wheel encoders, we can produce an estimate of where the robot is relative to the lane over time. 
 5. **Control**: Based on our estimate of where we are in the lane, we decide how to adjust the heading of the robot using a PID controller. 
 6. **Actuation**: Finally, these control values are applied to DC motors and the robot adjusts its movement. 
 
In the following sections we will provide a little bit more detail about how each of these components works. 
Afterwards, we provide some insight on how we can [tune the parameters](lane-following-parameter-tuning) of these
modules to achieve best performance. 

If you would like to dig a little bit deeper, take a look at the code. 
```{todo}
link
```

### Line detection

Line detection in the lane following pipeline involves extracting line segments from an image, 
focusing on specific colors that correspond to lane markers (white, yellow and red). 
This process combines multiple stages: color filtering, edge detection and line segment extraction. 
The approach is designed to efficiently detect lane lines in the Duckietown environment.

#### Preprocessing

The first step in the process is to preprocess the image for more effective feature extraction. 
For example, blurring the image using a Gaussian blur, converting the image to the HSV (hue, saturation, value) color space. 
HSV is preferred over RGB for color segmentation, as it separates chromatic content (hue) from intensity (value), 
making it easier to isolate specific colors. 
Then, a color range filter is applied to segment regions corresponding to marker colors (e.g., white, yellow, red). 
This operation results in a binary mask, highlighting only the regions of interest.

```{todo}
viewing the output of the color filter
```

#### Edge detection

Next, we have the edge detection. The filtered image is passed through the Canny edge detection algorithm to identify edges. This involves:

*   Gradient calculation: The image gradient is computed using the Sobel operator, which highlights areas of rapid intensity change.
    $ G = \sqrt{G_x^2 + G_y^2} $
    Where $G_x = \frac{\partial I}{\partial x}$ and $G_y = \frac{\partial I}{\partial y}$
*   Non-Maximum suppression: Thin out the edges by suppressing the pixels that are not part of the edge contours.
*   Hysteresis thresholding: Two thresholds ($T_{low}$ and $T_{high}$) are applied to classify edges as strong, weak or irrelevant. Edges stronger than $T_{high}$ are retained and weak edges connected to strong ones are kept.

```{todo}
how to view the edges
```


#### Line segment extraction

The detected edges are analyzed to extract line segments using the Hough line transform. This method identifies lines in the image by voting in the parameter space:

*   Each edge point $(x, y)$ contributes a vote for all possible lines passing through it, represented in polar coordinates as

    $$\rho = x\cos\theta + y\sin\theta, $$ 
    where $\rho$ is the distance from the origin to the line and $\theta$ is the angle of the line normal.

*   A threshold on the accumulator ensures that only lines with sufficient votes are retained.

Now, these are the main components involved, of course there is additional post processing steps that can be done as well as tuning of some hyperparameters to optimize performance of line detection.

```{todo}
how to view the line segments
```

### Ground Projection

Ground projection is a critical step in the lane localization pipeline, 
where detected line segments from the image are transformed into the robot’s 
2D ground plane reference frame. This transformation allows the Duckiebot to 
localize itself and navigate the environment effectively. 
The process relies on the homography matrix, which maps points from the 
camera’s image plane to the ground plane.



#### Homography and Calibration

The homography matrix is obtained through an extrinsic calibration procedure, 
which establishes the spatial relationship between the camera and the ground 
plane. Mathematically, the transformation is represented as:
$ P_w = HP_c$
where $P_w = (x, y, 1)$ and $P_c = (u, v, 1)$. $(u, v)$ are the pixel 
coordinates in the image. $(x, y)$ are the corresponding coordinates in the 
ground plane and $H$ is the 3x3 homography matrix.

#### Input and Processing

The node receives several inputs: line segments in pixel space and camera 
information (intrisic properties like focal length, principal point, etc.). 
The line segments are first rectified using the intrinsic parameters to 
correct distortions, ensuring accurate mapping.

#### Ouput

The projected line segments are represented in the robot’s reference frame 
on the 2D ground plane. This provides a useful representation for downstream 
tasks such as lane localization and control. Additionally, debug images 
showing rectified and projected views are published for verification.

```{todo}
how to view the projected segments
```

### Histogram filter for state estimation

The histogram filter is used to estimate the Duckiebot’s position within 
the lane, specifically its lateral deviation ($d$) and angular deviation 
($\phi$) relative to the lane center. 
This probabilistic approach provides a robust way to localize the robot 
using noisy sensor data while accounting for uncertainty.

#### Lane Pose Representation

The lane pose is represented as a tuple ($d$. $\phi$), 
where, as mentioned above $d$ is the lateral deviation from the lane 
center and $\phi$ is the angular deviation from the lane orientation. 
The filter maintains a discrete grid over the tuple values, 
where each grid cell represents a possible state of the robot.

```{todo}
pull some images from the notebooks?
```

This filter is *recursive*, which means that it iterates between 
*predicting* the next state of the robot, using the known kinematics of the 
model and the data from the wheel encoders, and then *updating* based 
on the information about where it is in the lane that comes from the 
ground projected lane segments. 

#### Prediction Step

During the prediction step, the filter uses the robot’s estimated linear and 
angular velocities to update the histogram, predicting how the lane pose 
evolves over time. The state transition is modeled based on the robot’s 
kinematic model:

$$
d_t = d_{t - 1} + v\Delta_t\cos\phi_{t - 1}
$$

$$
\phi_t = \phi_{t - 1} + \omega\Delta_t
$$

where $v$ is the linear velocity, $\omega$ is the angular velocity 
and $\Delta_t$ is the time step.

The predicted state probabilities are updated by shifting the histogram 
values accordingly.

#### Update Step

In the update step, the filter incorporates observations from the camera. 
Detected line segments are projected onto the ground plane and matched 
to the expected lane geometry. For each segment:

*   The filter computes votes for possible $(d, \phi)$ values based on the segment’s position and orientation.
*   These votes are added to the corresponding bins in the histogram.

This process updates the belief distribution, increasing confidence in 
states consistent with the observations.

The filter’s best estimate of the lane pose corresponds to the histogram 
cell with the highest value (maximum likelihood). 
This estimate is used to guide navigation.

```{todo}
add a visualization
```

### PID Controller for Lane Following

With the state estimation provided by the histogram filter, 
a PID controller is used to send wheel commands for the Duckiebot.

The PID controller calculates a control signal $u\_t$ based on the 
error e\_t between the desired state (plan/reference) and the estimated state:

$$ 
u_t = k_pe_t + k_i\int_0^te_{\tau}d\tau + k_d\frac{de_t}{d_t}
$$

Where:

*   $K_p$ is the proportional gain, addressing the current error.
*   $K_i$ is the integral gain, correcting cumulative past errors.
*   $K_d$ is the derivative gain, anticipating future errors based on the rate of change.

For lane following, the control inputs are the reference state 
$(d_{ref}, \phi_{ref})$, the control outputs (linear velocity $v$ (constant) 
and angular velocity $\omega$ (adjustable)) to correct deviations. 
Using a linearized kinematic model and a constant forward speed $v$, 
the control law simplifies to:  

$$u_t = K_dd + K_{\phi}\phi$$

where $K_d$ and $K_{\phi}$ are tuned proportional gains for lateral and 
angular errors, respectively.

(demo-lane-following-parameter-tuning)
## Debugging and Parameter Tuning

If you find the performance of your Duckiebot inconsistent or poor, here 
are some ways that you can try to debug the issue and tune the parameters
of the various modules.

```{tip}
You can always add a new file called `![ROBOTNAME].yaml` into the `config` 
folder in any package in the `dt-core` repo and those parameters will be 
taken at startup in place of the ones specified in `default.yaml`
```

```{tip}
In most cases, you can modify the parameters using the utility `rosparam set`. But 
take note that the values that you specify won't persist if you restart the demo until
you change the actual values that are loaded from the `config` folder of the node. 
```

### Tune the HSV thresholds

Use `dts gui` and `rqt_image_view` to view the colormaps, which are published to the topic
`![ROBOTNAME]/line_detector_node/debug/maps/compressed`. An example was shown above in Fig. TODO. 

You may want to tune the color thresholds in the line detector config if you find that 
the white or yellow regions of the image are not being well segmented. 

Specifically, look in the folder `packages/line_detector/config` and modify `default.yaml` 
or create your own `![ROBOTNAME].yaml` file. The color thresholds are specified by these 
thresholds:

```yaml
colors:
  RED:
    low_1: [0,140,100]
    high_1: [15,255,255]
    low_2: [165,140,100]
    high_2: [180,255,255]
  WHITE:
    low: [0,0,150]
    high: [180,100,255]
  YELLOW:
    low: [15,80,50]
    high: [45,255,255]
```
which are in HSV space as described above. You shouldn't need to worry about 
the `RED` ones for now but the `WHITE` and the `YELLOW` could need some tuning
depending on the type and amount of light in your environment.

### Verify the Ground Projections

If there was an error in your camera calibration, it will be very apparent when you look at the ground
projected segments. It should look like the top-down view of the lane as shown in Fig. XXX above.

Use `dts gui` and `rqt_image_view` to monitor the 
`![ROBOTNAME]/ground_projection_node/debug/ground_projection_image/compressed` topic 
or `RViZ` to view the lane pose and segment markers as described above.   
 
### Tune the PID Gains

Tuning of the gains is  one of the most important aspects for the stability and performance of the Duckiebot.

*   The proportional gain ($K_p$) affects the magnitude of corrections. Too high leads to oscillations, too low results in sluggish response.
*   The integral gain ($K_i$) addresses the steady-state errors but can introduce instability if over tuned.
*   The derivative gain ($K_d$) smooths the response by reducing overshoot but can amplify noise.

We performed tuning iteratively in our project by observing the robot’s response in different scenarios, such as sharp turns and straight paths and adjusting the gains to balance responsiveness and stability.




(demo-lane-following-troubleshooting)=
## Other Troubleshooting 

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
The Duckiebot does not drive nicely through intersections
---
For this demo, there should not be any intersections in the city layout. Duckiebots will interpret intersections as "broken" lanes, perceiving less salient features, potentially compromising the state estimate hence causing the driving troubles.
```


````{trouble}
The Duckiebot cuts white line while driving on inner curves (advanced)
---
This might be due to wrongly constructed lanes or bad Duckiebot calibrations. 
Fortunately, feedback control should take care of most of these problems.  

While running the demo modify the PID controller gains as indicated above.


````


```
Parts of this page were written by Adam Burhan and Azalée Robitaille at the
Université de Montréal
```