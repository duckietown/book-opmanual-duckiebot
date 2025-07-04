```{seo}
:description: The Dashboard.
:keywords: Duckietown, Duckiebot, Dashboard
```

(dashboard)=
# Dashboard

This chapter describes the `Dashboard`.

```{needget}
Completed [](handling).
---
Knowledge on the `Dashboard`.
```

## Introduction

```{vimeo} 527022343
```

To open the `Dashboard`, run the following command, where `PAGE` is an optional page (e.g., `robot/mission_control`):

```shell
dts duckiebot dashboard [--page PAGE] DUCKIEBOT_NAME
```

(dashboard-pages)=
## Pages

Once logged in, you will see a navigation panel on the left side of the `Dashboard`.

Note the pages in the table below.

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

In this tab, you can see your Duckiebot's name, type, configuration, [firmware](sd-card), temperature, CPU usage, etc.

```{figure} ../_images/software_tools/dashboard/dashboard_info.png
The `Info` tab on the `Robot` page of the `Dashboard`.
```

(dashboard-pages-robot-mission-control)=
#### Mission Control

In this tab, you can see what your Duckiebot sees, its lateral and angular speed, and a plot of its left and right motor speeds.

```{figure} ../_images/software_tools/dashboard/dashboard_mission_control.png
The `Mission Control` tab on the `Robot` page of the `Dashboard`.
```

(dashboard-pages-robot-health)=
#### Health

In this tab, you can see a plot of your Duckiebot's temperature, CPU usage, etc.

```{figure} ../_images/software_tools/dashboard/dashboard-health.png
The `Health` tab on the `Robot` page of the `Dashboard`.
```

(dashboard-pages-robot-architecture)=
#### Architecture

In this tab, you can see a graphical representation of your Duckiebot's ROS network.

```{figure} ../_images/software_tools/dashboard/dashboard-architecture.png
The `Architecture` tab on the `Robot` page of the `Dashboard`.
```

(dashboard-pages-portainer)=
### Portainer

On this page, you can manage your Duckiebot's Docker containers.

```{figure} ../_images/software_tools/dashboard/dashboard-portainer.png
The `Portainer` page of the `Dashboard`.
```
