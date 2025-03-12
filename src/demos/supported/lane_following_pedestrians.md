```{seo}
:description: Duckietown lane following with obstacles autonomous behavior demo. 
:keywords: duckietown, demo, autonomous driving, demonstration, duckiebot, db21, db21-j4, AV, autonomous vehicle, self-driving car, self-driving, robot autonomy, AI robotics
```

(demo-lane-following)=
# Lane following with Obstacles (`LFP`)

```{needget}
* An assembled and initialized Duckiebot;
* [Wheels calibration](wheel-calibration) completed;
* [Camera calibration](camera-calib) completed;
* [Joystick demo](rc-control) has been successfully launched;
* A Duckietown city loop, as detailed in the [appearance specifications](book-opmanual-duckietown:book).
---
* A Duckiebot driving autonomously in a Duckietown city loop with obstacles.
```

```{admonition} Difficulty Level
Easy
```

(demo-lane-following-obstacles-expected)=
## Expected results

```todo
record results
```


(demo-lane-following-obstacles-duckietown-setup)=
## Duckietown setup notes

Before getting started, make sure your Duckietown is ready to go:
- The layout adheres to the [](book-opmanual-duckietown:book);
- The lighting is "good": ideally white diffused light. This demo relies on images from the camera and 
  color detections, so avoid colored lights, reflections or other conditions that might confuse or blind 
  the onboard image sensor;


(demo-lane-following-obstacles-duckiebot-setup)=
## Duckiebot setup notes

* Duckiebot in configuration [DB21M, DB21J, or DB19](duckiebot-configurations). 
* The Duckiebot is powered on and connected to your network. You should be able to successfully ping it from your base station;
* You are able to [see what the Duckiebot sees](make-it-see);
* You are able to [remote control](rc-control) your Duckiebot; 
* The [camera is calibrated](camera-calib);
* The [wheels are calibrated](wheel-calibration).

(demo-lane-following-obstacles-pre-flight)=
## Pre-flight checklist

* Place the Duckiebot inside a lane (driving on the right-hand side of the road), making sure it sees the lane lines;
* Place some larger obstacles on the road

(demo-lane-following-obstacles-run)=
## Demo instructions

The instructions for running this demo are almost identical as the [procedure for running
 the lane following demo](demo-lane-following-run), except we will use a different launcher. 
 These instructions are:
 
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
dts matrix run --standalone -m assets/duckiematrix/maps/loop_with_pedestrians
```

```{note}
This is a different map than the one used for the [Lane Following Demo](demo-lane-following) since 
now we have duckie pedestriancs crossing the street. 
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

In this case, different than the basic [Lane Following Demo](demo-lane-following), now if there
is an obstacle in the path that is big enough to be detected by the **time-of-flight** sensor (the little black square on 
the front bumper), and you will see the LEDs all turn <blue>BLUE</blue> indicating that an obstacle
is detected. If the obstacle is removed, the Duckiebot will return to lane following behavior. 


If things are not working as expected, please look at the [](demo-lane-following-parameter-tuning) or 
[](demo-lane-following-troubleshooting) sections for suggestions. 

You can also look at the same visualizations. 

A specific signal you may be interested to observe is the range value that is being output by the time-of-flight
sensor. To monitor it, a good way could be to do:

`dts gui ![ROBOTNAME]`

and then in the resulting terminal, open up an `rqt_plot` window. In the top left, select the topic
`![ROBOTNAME]/tof_driver_node/front_center_tof/range`.

## How it Works

The method of lane following is the same as [](demo-lane-following-how-it-works). The additional 
complexity here is due to the use of the **time-of-flight** sensor which is mounted on the 
front bumper of your Duckiebot. Every time the reading from that sensor 
drops below a certain threshold that is specified by a file in the 
`packages/obstacle_detection/tof_obstacle_detection_node` folder (either `default.yaml` or `![ROBOTNAME].yaml` 
if you have created it).

You might look at the `tof_obstacle_detection_node` source code (in `packages/obstacle_detection/src/tof_obstacle_detection_node.py`
and ask yourself exactly how this is causing the robot to stop when the range is too low. 
The answer is through a **finite state machine** or FSM.

To understand this better, take a look at the file in `packages/fsm/config/lane_following_pedestriancs.yaml`. This file
specifies what `events` cause the FSM to transition states. In this case we can see:

```yaml
  obstacle_detected:
    topic: "tof_obstacle_detection_node/obstacle_detected"
    msg_type: "BoolStamped"
    trigger: True
  obstacle_cleared:
    topic: "tof_obstacle_detection_node/obstacle_cleared"
    msg_type: "BoolStamped"
    trigger: True
```
in the list of events which are the topics that are published by the `tof_obstacle_detection_node`.
Furthermore, if we look further below in the config file we can see 

```yaml
  LANE_FOLLOWING:
    transitions:
      obstacle_detected: "STOP"
```

Which indicates that the `obstacle_detected` event occuring will cause the FSM
to transition to state `STOP` if it is presently in state `LANE_FOLLOWING`. 

This still doesn't explain how the robot actually stops though. There is another node which helps with that
called the `car_cmd_switch_node` whose configuration is located in `robots/duckiebot/dagu_car/config/car_cmd_switch_node`.
If we look at the `default.yaml` file in that folder we see a set of `mappings` which indicate which
topic that produces control commands should be considered active for any given state. In there, we see 
the following mappings:

```yaml
mappings: #Mapping from FSMStates.state to cmd source names. Allows different FSM mode to use the same source.
  NORMAL_JOYSTICK_CONTROL: "joystick"
  LANE_FOLLOWING: "lane"
  STOP: "stop"
``` 
This effectively acts as a multiplexer deciding which controller to actually connect to the 
wheels depending on the state output from the FSM. 

Here we can see that in the `STOP` mode we connect the `simple_stop_controller_node` to the wheels
which has the effect of stopping them. 


## Parameter Tuning

In this case there is really only one parameter that could be tuned, and that is the 
threshold used by the `tof_obstacle_detection_node`. Tuning this will result in 
the stopping of the Duckiebot being triggered by obstacles that are further away. 
But be careful, if you make it too large, the Duckiebot stopping could be triggered by 
undesirable things (such as obstacles that are not actually in the road or by the road itself).