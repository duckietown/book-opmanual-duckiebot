(laptop-setup)=
# Setup - Laptop

```{needget}
* A laptop or machine running Ubuntu 20.02 or 22.04
* Alternatively: A laptop or machine running MacOS
---
* Your laptop configured with Duckietown software and ready to run Duckietown robots and learning experiences
```

In this section, we will install all the software that you need to run the Duckietown development environment on 
your laptop.  This includes Git, Docker, and the Duckietown Shell.

```{note}
If you are unfamiliar with Git or Docker, we strongly recommend reading the following reference pages to gain a 
working understanding of these tools.

1. [The Duckietown Intro to Git](version_control_with_git)
2. [The Duckietown Intro to Docker](preliminaries-docker-basics)
```

Check out the laptop requirements below to make sure you are ready to proceed, then continue on to the next page to 
begin setting up your development environment.  If you need help installing Ubuntu, see [Step 0: System Installation](system-installation) 
below.

## Minimal Laptop Requirements

Duckietown officially supports Ubuntu 20.04 and Ubuntu 22.04.

Please be aware that using an operating system that is not officially supported reduces the ability of the 
Duckietown team and the whole community to provide you with technical support when needed.

```{list-table}
:name: supported-os

* - **Officially Supported**
  - 
* - Ubuntu 22.04
  - This is the recommended operating system for using Duckietown. We strongly suggest using it.
* - Ubuntu 20.04
  - This older version of the Ubuntu operating system will currently work with the Duckietown ecosystem.
* - **Unofficially Supported**
  - 
* - Other Linux distributions
  - Having Ubuntu is not an enforced requirement, and everything should in theory work on any Linux operating system. 
* - MacOSX
  - We provide instructions for setting up on MacOSX, but you may run into bugs as you venture further into 
  development.
* - Ubuntu installed via VM
  - This is possible, though network configuration is required.  See the section below for more 
  details.
* - **Not Supported**
  - 
* - Windows
  - Currently, it is not possible to run the Duckietown development tools on Windows. See below for 
  available VM options to run Ubuntu on your Windows machine.
```

### Native installation vs virtual machines

Having Ubuntu installed natively on your laptop is recommended but not strictly required.

If you are running Ubuntu in a VM make sure that you are using a Bridged network adapter
(for example VirtualBox uses NAT by default). This allows you to be on the same subnetwork
as your Duckiebot.

Sometimes when running a VMware machine on a Mac OS host, it is neccessary to have two
network adapters: _Share with my Mac_ for connecting to the internet and _Bridged Networking_
for connecting to the Duckiebot.

For more information about networking with VMware, see [here](https://wiki.ros.org/ROS/NetworkSetup).

(system-installation)=
## Step 0: System Installation

`````{tab-set}

````{tab-item} Ubuntu
Install the Ubuntu operating system. Ubuntu 22.04 is strongly suggested.

Follow the 
[official documentation](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop)
for instructions.
````

````{tab-item} MacOSX

```{warning}
This configuration is not officially supported. We recommend using the Ubuntu Operating System for an 
optimal experience.
```

Select the MacOSX tab on each of the following laptop setup pages to follow the 
instructions specific to your operating system.
````

`````