# Additional Software Tools

```{seo}
:description: Additional software tools.
:keywords: Duckietown, Duckiebot, additional software tools
```

This chapter describes additional software tools.

```{needget}
Completed [](sw-tools-ui-dashboard).
---
Knowledge on additional software tools.
```

(gui)=
## GUI tools

To open a terminal with access to your Duckiebot's ROS network, run:

```shell
dts gui DUCKIEBOT_NAME
```

```{note}
Only a single instance of the `start_gui_tools` container can exist on your computer at a time. If multiple terminal instances are required, use [](novnc).
```

(novnc)=
### noVNC

To open a desktop environment connected to your Duckiebot, run:

```shell
dts gui --vnc DUCKIEBOT_NAME
```

To open a terminal within this desktop environment, click the `Terminal` desktop icon.

(ros)=
## ROS

```{note}
The following requires a terminal with access to your Duckiebot's ROS network.
```

### How to see a list of topics

To see a list of topics, run:

```shell
rostopic list
```

````{note}
The following topics should be present:

```shell
/DUCKIEBOT_NAME/camera_node/camera_info
/DUCKIEBOT_NAME/camera_node/image/compressed
/rosout
/rosout_agg
```
````

### How to see the publishing frequency for a topic

To see the publishing frequency for a topic, run the following command, where `TOPIC` is the topic (e.g., `/DUCKIEBOT_NAME/camera_node/image/compressed`):

```shell
rostopic hz TOPIC
```

````{note}
For a Raspberry Pi 3, you should see a publishing frequency of around `30 Hz` for the `/DUCKIEBOT_NAME/camera_node/image/compressed` topic:

```shell
average rate: 30.016
    min: 0.026s max: 0.045s std dev: 0.00190s window: 841
```
````

To stop `rostopic hz TOPIC`, press <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### How to see messages being sent to a topic

To see messages being sent to a topic, run the following command, where `TOPIC` is the topic (e.g., `/DUCKIEBOT_NAME/camera_node/image/compressed`):

```shell
rostopic echo TOPIC
```

```{note}
For the `/DUCKIEBOT_NAME/camera_node/image/compressed` topic, you should see a large sequence of numbers being printed to your terminal.
```

(rqt-novnc)=
### How to see what your Duckiebot sees

To see what your Duckiebot sees, run the following command and select the `/DUCKIEBOT_NAME/camera_node/image/compressed` topic from the drop-down menu:

```shell
rqt_image_view
```

```{note}
If you are using [](novnc), you can also click the `RQT Image View` desktop icon.
```

```{figure} ../_images/software_tools/additional_software_tools/rqt_image_view.png
The `rqt_image_view` window with the `/DUCKIEBOT_NAME/camera_node/image/compressed` topic dropdown menu option shown.
```

(rqt-graph-novnc)=
### How to see a graphical representation of your Duckiebot's ROS network

To see a graphical representation of your Duckiebot's ROS network, run:

```shell
rqt_graph
```

## Troubleshooting

```{trouble}
My ROS commands are not working and I cannot use <kbd>Tab</kbd> to autocomplete any ROS commands.
---
Run:

    `source /code/catkin_ws/devel/setup.bash`
```

```{trouble}
I cannot connect to my Duckiebot's ROS Master.
---
Run the following command and make sure that the `ROS`, `car-interface` and `duckiebot-interface` containers are running:

    `dts duckiebot dashboard DUCKIEBOT_NAME --page portainer`
```
