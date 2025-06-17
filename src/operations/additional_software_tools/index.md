```{seo}
:description: Additional software tools for a Duckiebot.
:keywords: Duckietown, Duckiebot, gui, novnc, ROS
```

(ops-tools)=
# Operation - Additional Software Tools

This section describes how to use additional software tools for your Duckiebot.

(gui)=
## GUI tools

To open a terminal with access to your Duckiebot's ROS network, run:

    dts gui ![DUCKIEBOT_NAME]

```{note}
Only a single instance of the `start_gui_tools` container can exist on your computer at a time. If multiple terminal instances are required, use [](novnc).
```

(novnc)=
### noVNC

To open a desktop environment connected to your Duckiebot, run:

    dts gui --vnc ![DUCKIEBOT_NAME]

To open a terminal within this desktop environment, click the `Terminal` desktop icon.

(ros)=
## ROS

Once you have opened a terminal with access to your Duckiebot's ROS network, you can do the following using that terminal.

### See a list of topics

To see a list of topics, run:

    rostopic list

```{note}
The following topics should be present:

    /![DUCKIEBOT_NAME]/camera_node/camera_info
    /![DUCKIEBOT_NAME]/camera_node/image/compressed
    /rosout
    /rosout_agg
```

### See the publishing frequency for a topic

To see the publishing frequency for a topic, run the following command, where `![TOPIC]` is the topic (e.g., `/![DUCKIEBOT_NAME]/camera_node/image/compressed`):

    rostopic hz ![TOPIC]

```{note}
For a Raspberry Pi 3, you should see a publishing frequency of around `30 Hz` for the `/![DUCKIEBOT_NAME]/camera_node/image/compressed` topic:

    average rate: 30.016
        min: 0.026s max: 0.045s std dev: 0.00190s window: 841
```

To stop `rostopic hz ![TOPIC]`, press <kbd>Ctrl</kbd>-<kbd>C</kbd>.

### See messages being sent to a topic

To see messages being sent to a topic, run the following command, where `![TOPIC]` is the topic (e.g., `/![DUCKIEBOT_NAME]/camera_node/image/compressed`):

    rostopic echo ![TOPIC]

```{note}
For the `/![DUCKIEBOT_NAME]/camera_node/image/compressed` topic, you should see a large sequence of numbers being printed to your terminal.
```

(rqt-novnc)=
### See what your Duckiebot sees

To see what your Duckiebot sees, run the following command and select the `/![DUCKIEBOT_NAME]/camera_node/image/compressed` topic from the drop-down menu:

    rqt_image_view

```{note}
If you are using [](novnc), you can also click the `RQT Image View` desktop icon.
```

```{figure} ../../_images/assembly_setup/rqt_image_view.png
:name: rqt_dropdown

The `rqt_image_view` window with the `/![DUCKIEBOT_NAME]/camera_node/image/compressed` topic dropdown menu option shown.
```

(rqt-graph-novnc)=
### See a graphical representation of your Duckiebot's ROS network

To see a graphical representation of your Duckiebot's ROS network, run:

    rqt_graph

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

    `dts duckiebot dashboard ![DUCKIEBOT_NAME] --page portainer`
```
