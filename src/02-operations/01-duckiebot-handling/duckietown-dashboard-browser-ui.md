(sw-tools-ui-dashboard)=
# Duckiebot Dashboard

```{seo}
:description: The Dashboard is a browser-based UI for Duckiebots, enabling convenient hardware and software debugging.
:keywords: Duckietown, Duckiebot, Dashboard, browser-based UI, UI, debugging
```

This chapter describes the Duckietown Duckiebot Dashboard (also known as just "the Dashboard"), i.e., a browser-based interface for Duckiebots (and Duckiedrones).

```{needget}
- Duckiebot Dashboard correctly set up: [](duckiebot-dashboard-setup). 
---
- Understanding of the Duckiebot Dashboard resources. 
```


## Introduction to the Duckietown Dashboard

```{vimeo} 527022343
:alt: introduction to the duckietown dashboard for duckiebot browser-based diagnostics
```

To open the Dashboard, run the following command, where `PAGE` is an optional page (e.g., `robot/mission_control`):

```shell
dts duckiebot dashboard [--page PAGE] DUCKIEBOT_NAME
```

(dashboard-pages)=
## Dashboard Pages

Once logged in, you will see a navigation panel on the left side with links to:

```{list-table}
:header-rows: 1
:name: table:dashboard-pages

* - Page
  - Description
* - File Manager
  - A tool for managing the files on your Duckiebot
* - Portainer
  - A tool for managing the containers on your Duckiebot
* - Robot
  - Provides information about the status of your Duckiebot
* - Users
  - Allows multiple accounts to use a single Duckiebot
* - Profile
  - Provides information about your Duckietown account
* - Package Store
  - Provides available packages for your Duckiebot
* - Settings
  - Allows the configuration of the `Dashboard` to be changed manually
```

(dashboard-pages-robot)=
### Robot

On this page, you can find several tabs related to your Duckiebot.

(dashboard-pages-robot-info)=
#### Info

In this tab, you can see your Duckiebot's name, type, configuration, firmware (i.e., the version number of the image flashed on your SD card at [](setup-db-sd-card-flashing-intro)), temperature, CPU usage, etc.

```{figure} ../../_images/software_tools/dashboard/dashboard_info.png
:name: dashboard-info
:align: center
:width: 80%
:alt: The Info tab on the Robot page of the Duckietown Duckiebot Dashboard

The **Info** tab on the **Robot** page of the Dashboard.
```

(dashboard-pages-robot-mission-control)=
#### Mission Control

In this tab, you can see what your Duckiebot sees, its lateral and angular speed, and a plot of its left and right motor speeds.

```{figure} ../../_images/software_tools/dashboard/dashboard_mission_control.png
:name: dashboard_mission_control
:align: center
:width: 80%
:alt: The Mission Control tab on the Robot page of the Dashboard. of the Duckietown Duckiebot Dashboard

The **Mission Control** tab on the **Robot** page of the Dashboard.
```

(dashboard-pages-robot-health)=
#### Health

In this tab, you can see a plot of your Duckiebot's temperature, CPU usage, etc.

```{figure} ../../_images/software_tools/dashboard/dashboard-health.png
:name: dashboard-health
:align: center
:width: 80%
:alt: The Health tab on the Robot page of the Dashboard.

The **Health** tab on the **Robot** page of the Dashboard.
```

(dashboard-pages-robot-architecture)=
#### Architecture

In this tab, you can see a graphical representation of your Duckiebot's ROS network.

```{figure} ../../_images/software_tools/dashboard/dashboard-architecture.png
:name: dashboard-architecture
:align: center
:width: 80%
:alt: The Architecture tab on the Robot page of the Dashboard.

The **Architecture** tab on the **Robot** page of the Dashboard.
```

(dashboard-pages-portainer)=
### Portainer

On this page, you can manage your Duckiebot's Docker containers.

```{figure} ../../_images/software_tools/dashboard/dashboard-portainer.png
:name: dashboard-portainer
:align: center
:width: 80%
:alt: The Portainer page of the Dashboard.

The **Portainer** page of the Dashboard.
```
