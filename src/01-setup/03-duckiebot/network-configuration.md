(setup-duckiebot-network)=
# Network Configuration in Duckietown

```{seo}
:description: It is said 90% of problems in robotics stem from networks. Learn how to avoid them by setting your networks up correctly for Duckietown.
:keywords: Duckietown, Duckiebot, network setup, networks
```

```{needget}
* [An initialized Duckiebot](duckiebot-boot)
* A network router with internet connection
* (optional) an ethernet cable 
---
* Learn how to change network configuration on the Duckiebot
* Basics for debugging network challenges
* A connected Duckiebot
```

Most `dts` commands rely on the connectivity between the Duckiebot, the computer used to interact with it, and the internet. 

To make sure all commands work, the Duckiebot and the computer must:

* appear as physical devices on a same subnet;
* the network should have access to the internet.

```{warning}
Networks are the most common blocker when using Duckietown. Making sure this step is completely correctly will remove many future headaches. 
```

## Wi-Fi connection

Setting up a working Wi-Fi connection between your base station and Duckiebot is a prerequisite for smooth operations.

### Checkpoint

Your network is set up correctly if you can:

    ping ROBOT_NAME.local

while being connected to the internet. You can test this by opening a browser, or, e.g., 

    ping 8.8.8.8


````{testexpect}
Run:

```shell
dts fleet discover
```
---
```{figure} ../../_images/setup/handling/fleet_discover.png
:name: fig:fleet-discover-2
:alt: duckiebot ready on dts fleet discover network discovery tool
:width: 85%

Output of `dts fleet discover` with a connected Duckiebot
```
````


(setup-duckiebot-edit-networks)=
## How to add or edit Wi-Fi networks on a Duckiebot

It is possible to add, remove, or edit networks to which a Duckiebot will connect to by editing the network configuration file, **without** the need to re-flash the SD card. To do so, one must edit the `/etc/wpa_supplicant.conf` file on the Duckiebot's SD card: [](duckiebot-setup-wifi).


(setup-uni-network)=
### A word on "corporate" networks, e.g., `eduroam`

Some university networks (e.g., the global `eduroam`) have multiple layers of authentication, i.e., a password is not sufficient to access the network. In these cases, the default network configuration settings used by Duckietown are insufficient to connect to the network. 

It is possible to edit the `wpa_supplicant.conf` file in your Duckiebot to connect to `eduroam`, but data specific to your university will be required. You will have to coordinate with your network administrator to find out this data. 

Here is an [example `wpa_supplicant.conf` setup for the University of Bristol `eduroam`](https://www.wireless.bris.ac.uk/eduroam/instructions/go-wpasup/).

(setup-router)=
## Prerequisites of router and internet connection

Ideally, you work with Duckietown in an environment in which you have administrator powers over the available network. This is the typical case for home networks or, e.g., phone hot spots.

In university or corporate networks, for security reasons, some functionalities like local discovery or access to certain ports or websites are made unavailable. Duckietown relies on:

- a router being able to resolve `ROBOT_NAME.local` and local IP address (i.e., local discovery tools like mDNS working);
- access to the internet (e.g., GitHub, DockerHub, Duckietown, etc.).

These tools are typically deactivated in corporate networks, like in universities or companies. If this is the case of your working environment, ask your IT team to provide a subnet with internet access and enabled discovery tools. In the meantime you could:

- use a phone (with unlimited data plan) as hot spot;
- work from your home network;
- create a temporary "pirate" network by plugging in a router at work while your IT figures out the main network settings. 


## Ethernet connection between Duckiebot and Base Station

For debugging Wi-Fi connections it might be useful to occasionally connect the computer and Duckiebot through an ethernet connection. The simplest option, when you have physical access to the router, is to connect the Duckiebot via ethernet cable to the router itself. In this way it should immediately appear on the network (e.g., discoverable through `dts fleet discover`).


```{todo}
describe procedure to connect computer directly to duckiebot via ethernet cable
```
<!--
Direct connections between computer and Duckiebot (...)
-->