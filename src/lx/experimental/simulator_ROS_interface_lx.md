(lx-simulator-ros)=
# Creating a Simulator ROS Wrapper

```{note}
This exercise is likely out of date
```

```{needget}
The simulator installed accoring to [these instructions](book-devmanual-software:duckietown-simulation)
---
The ability to run a ROS agent using the simulator as if it was a robot
```

How would we be able to exploit the powerhouse of dt-core in this simulator? 
By creating a ROS interface to the simulator! This will allow us to run the same 
code that we run on the duckiebot on the simulator.

In this exercise, you will create a ROS wrapper that maps wheel commands to 
actions and observations to camera images on a ROS topic.

To do so, you will leverage the skills you have obtained in the previous 
exercises where you used a ROS package template and created your own publisher and 
subscriber. This time, we encourage you to again use the ROS package template 
and to create a node which can both publish and subscribe to topics.

[This link](https://drive.google.com/file/d/1BU17Gkl5wEjvxv0OtZ2bv5EbcyyH09ZN/view) 
contains some important files that will be required to properly test your ROS wrapper. 
The `docker-compose.yaml` file spins up several containers at once through the 
simple command `docker-compose up` from the directory where the file resides. 
If you take a peek at the file you will see that these containers have familiar names.
They are used to provide functionality to your Duckiebot, and in this scenario 
they are still needed to allow you to run demos in the simulator, 
to use the virtual joystick, etc. Inside `docker-compose.yaml` there are some lines which you will have to modify. You have to make sure that the data folder that you have downloaded from the link above is mounted on the containers so that the simulator is able to use your calibration and other configuration files. 

Since now we are running our code on a fake robot (which is really our local machine) we need to modify a few things. In your `/etc/hosts` file, you will have to add the line `127.0.0.1     fakebot.local`. At the end of the Dockerfile in your ROS project (based on the Duckietown template) add the line: `ENV VEHICLE_NAME fakebot`.

Some apt packages you will need are: `freeglut3-dev`, `xvfb`

You will also need the `duckietown-gym-daffy` pip3 package

Finally, to ensure your publishers and subscribers parse the same ROS messages as the rest of the Duckietown pipeline, you might want to make use of `duckietown_msgs` (which is just a ROS package defined in [`dt-ros-commons`](https://github.com/duckietown/dt-ros-commons/tree/daffy/packages/duckietown_msgs)).

Since your containers don't have a display, you will want to run these lines of bash code inside your container before running the wrapper.

```bash
dt-exec Xvfb :1 -screen 0 1024x768x24 -ac +extension GLX +render -noreset 
export DISPLAY=:1
```

### Troubleshooting

```{trouble}
Despite following the above instructions, when I run my container I get an error like 
`pyglet.canvas.xlib.NoSuchDisplayException: Cannot connect to "None"`
---
It could be that display :1 is in use or cannot be used by the docker container. 
Try to change the display number to a higher number (e.g. :33). 
Check out [this post](https://stackoverflow.com/c/duckietown/questions/103) for more 
details.
```