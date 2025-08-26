(setup-sw-intro)=
# Setup - Software

```{seo}
:description: Learn how to set up your base station (laptop, desktop) to work with Duckietown robots and simulators. This is the first step in getting started with Duckietown.
:keywords: Duckietown, Duckiebot, computer setup, set up, preparation, base station, getting started
```

This chapter describes how to install software needed to work with Duckietown. 

```{needget}
* A computer with at least `50 GB` of free space running [Ubuntu 22.04 or newer](setup-computer).
* A [GitHub account](setup-account-github).
* A [Docker Hub account](setup-account-docker).
* A [Duckietown account](setup-account-duckietown-hub).
* An [SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
* An Internet connection.
* Approximately 30 minutes.
---
A computer set up to use Duckietown and interact with Duckiebots. 
```

```{attention}
Every time you read `DUCKIEBOT_NAME` or `ROBOT_NAME`, replace it with your Duckiebot's `HOSTNAME`, (omitting `.local` at the end).
```

```{note}
<kbd>Key</kbd> indicates a keyboard key.
```

(setup-computer-vm-vs-native-ubuntu)=
## Native Ubuntu installation and Virtual Machines (VM)

Running Ubuntu natively is _strongly_ recommended but not strictly required.

If you are running Ubuntu in a VM (Virtual Machine), make sure that your computer and Duckiebot appear as physical entities on the same network. This is achieved by selecting the "bridged network adapter" (e.g., VirtualBox uses NAT by default), which will allow you to be on the same subnetwork as your Duckiebot.

```{note}
When running a VMware machine on a macOS host, it may be necessary to have the following network adapters:
* `Share with my Mac` (for connecting to the Internet).
* `Bridged Networking` (for connecting to your Duckiebot).
```

If using a M-series Mac (ARM architecture), some success has been achieved by emulating a x86 architecture using [UTM](https://mac.getutm.app/).  

```{attention}
While VMs on different host OS might work:
1. We _strongly_ reccomend using a native (or, dual boot) Ubuntu installation, especially if it is your first run with Duckietown
2. Only native Ubuntu setups are officially supported by the Duckietown team (community resources are still available for other setups). 
```

## In this Section

```{tableofcontents}
```