```{seo}
:description: How to use the Dashboard.
:keywords: Duckietown, Duckiebot, Dashboard
```

(duckiebot-dashboard-use)=
# Operation - Use the Dashboard

This section describes how to use the `Dashboard`.

To open the `Dashboard`, run:

    dts duckiebot dashboard ![DUCKIEBOT_NAME]

To open a specific page on the `Dashboard`, run the following command, where `![PAGE]` is the page (e.g., `robot/mission_control`):

    dts duckiebot dashboard ![DUCKIEBOT_NAME] --page ![PAGE]

(dashboard-overview)=
## Pages

```{vimeo} 527022343
```

Once logged in, you will see a navigation panel on the left side of the `Dashboard`.

Note the pages in the table below.

```{list-table}
:header-rows: 1
:name: dashboard-pages

* - Page
  - Description
* - File Manager
  - A tool for managing the files on a Duckiebot
* - Portainer
  - A tool for managing the containers on a Duckiebot
* - Robot
  - Provides information about the status of a Duckiebot
* - Users
  - Allow multiple accounts to use one Duckiebot
* - Profile
  - Provides information about a Duckietown account
* - Package Store
  - Provides available packages for a Duckiebot
* - Settings
  - Allows the configuration of the `Dashboard` to be changed manually
```

(dashboard-robot)=
### Robot

On this page, you can find several tabs related to your Duckiebot.

(dashboard-robot-overview)=
#### Info

In this tab, you can find information about your Duckiebot, including its name, type, configuration, CPU usage, temperature, etc.

```{figure} ../../_images/assembly_setup/dashboard_info.png
:name: dashboard_info_tab
```

```{note}
In this tab, you can find your Duckiebot's [firmware version](setup-duckiebot-sd-card).
```

(dashboard-mission-control)=
#### Mission Control

In this tab, you can see what your Duckiebot sees, its lateral and angular speed, and a plot of its left and right motor speeds.

```{figure} ../../_images/assembly_setup/dashboard_mission_control.png
:name: dashboard_mission_control_tab
```

(dashboard-robot-health)=
#### Health

In this tab, you can see a plot of your Duckiebot's temperature, frequency and CPU usage.

```{figure} ../../_images/assembly_setup/dashboard-health.png
:name: dashboard_health_page
```

(dashboard-robot-architecture)=
#### Architecture

In this tab, you can see the a graphical representation of the ROS network on your Duckiebot.

```{figure} ../../_images/assembly_setup/dashboard-architecture.png
:name: dashboard_architecture_page
```

(dashboard-portainer)=
### Portainer

On this page, you can manage the containers on your Duckiebot.

```{figure} ../../_images/assembly_setup/dashboard-portainer.png
:name: dashboard_portainer_page
```
