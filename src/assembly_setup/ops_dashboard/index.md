(duckiebot-dashboard-use)=
# Operation - Use the Dashboard

This section shows how to use the Duckietown Dashboard on the Duckiebot.

(dashboard-overview)=
## What is in the Dashboard?

The following video provides a brief tour of the most important features
of the Duckietown Dashboard on your Duckiebot.

<div figure-id="fig:howto-dashboard-use" figure-caption="Dashboard operation tutorial.">
<dtvideo src="vimeo:527022343"/>
</div>

To see all the available dashboard components, you will need to first log in. Once logged into the dashboard, you will see a navigation panel down the left side of the page. The 7 available subpages are:


```{list-table}
:header-rows: 1
:name: dashboard-pages

* - PAGE NAME
  - DESCRIPTION
* - Portainer
  - A nice GUI tool for seeing all containers running on a Duckiebot
* - File Manager
  - A file manager for managing the files on the robot
* - Robot
  - A summary page for the robot status
* - Profile
  - Information for your duckietown account
* - Package Store
  - A package store contain all available packages for your Duckiebot
* - Users
  - Advanced Feature: Allow multiple students to use one Duckiebot
* - Settings
  - Advanced Feature: Change configuration of your Duckiebot dashboard manually
* - Restful API
  - Advanced Feature: Documentation to the RestAPI exposed by the Dashboard.
```

Let's dive into a few pages that you will need to get started.

(dashboard-robot)=
## The Robot Page

In this page you will find several tabs that help you see and understand the status of your Duckiebot. The default tab is `Info`.

(dashboard-robot-overview)=
### Robot - Info

In this tab, you can find information for your robot - including your robot name, type, configuration, and critical information such as CPU usage, temperature, and other crucial robot vitals.

```{figure} ../../_images/assembly_setup/dashboard_info.png
:name: dashboard_info_tab
```

```{note}
From this page you can read the Duckiebot's firmware version, i.e., the version of the base image used during [initialization](setup-duckiebot). This might inform if a re-initialization is needed, e.g., to perform the `DB21` [battery update](howto-db21m-battery-update).
```

(dashboard-mission-control)=
### Robot - Mission Control

This is the Mission Control tab.

```{figure} ../../_images/assembly_setup/dashboard_mission_control.png
:name: dashboard_mission_control_tab
```

In this tab you can see what the Duckiebot sees via the iamge stream, the lateral and angular speed of your robot, and a plot of left and right motor speed.
This is the tab that lets you monitor and control your Duckiebot.

```{tip}
The page contains 4 blocks by default.
Feel free to drag them around and rearrange them as you please.
You can also use the menu button of each block to resize them.
```

```{trouble}
I do not see the camera image on the dashboard.
---
This could be caused by a few issues. Make sure you are accessing the dashboard using `https://ROBOT_HOSTNAME.local/` instead of directly accessing the dashboard using robot IP address. Make sure the lens cap has been removed from your camera. If you still don't see an image, jump to the [Operation - Make it See](make-it-see) page for more debugging options.
```

(dashboard-robot-health)=
### The Health Page

This is the Health Page. It will show you a plot of the robot's health status such as temperature, frequency, and CPU usage. It is a good debugging tool to watch your code's resource usage.

```{figure} ../../_images/assembly_setup/dashboard-health.png
:name: dashboard_health_page
```

(dashboard-robot-architecture)=
### The Architecture Page

This is the Architecture Page. It will allow you to visualize all the published ROS topics and see their details. It is a useful tool to see what is running and what is not. You can also use this tool as a replacement of `rqt-graph`. For more instructions on rqt-graph, you can see it [here](rqt-graph-no-vnc)

```{figure} ../../_images/assembly_setup/dashboard-architecture.png
:name: dashboard_architecture_page
```

(dashboard-portainer)=
## The Portainer Page

Portainer is a provided tool for managing all the docker containers that are running on the Duckiebot. Using portainer tools, you can quickly see the status of the containers on your Duckiebot.

```{figure} ../../_images/assembly_setup/dashboard-portainer.png
:name: dashboard_portainer_page
```

You can select **containers** to see all the containers on the Duckiebot.

For more information about portainer, you can find them in [this](#sub:dashboard-portainer) page.

(drive-dashboard)=
## Drive your Duckiebot via mission control

You can remotely drive your Duckiebot through mission control page.

The first thing to check to make sure that everything we have done so far
is correct, is the status of the **Bridge**, in the top-right corner of the page.
The label should show the status "**Bridge: Connected**" (as shown in the image above).
If the indicator reads "**Bridge: Closed**", it means that something went wrong
while launching the ROS websocket node above. In that case, start again from
the beginning of this section.

```{note}
Don't worry if one of the blocks is called "Camera" but you
don't see an image. We will get to that later.
```

Toggle the **Take over** switch
in the top-right corner of the page to gain control of your robot.
You will see that the background of the page will highlight and the
central plot will start moving.

You can now use the arrows on your keyboard to drive your Duckiebot.
