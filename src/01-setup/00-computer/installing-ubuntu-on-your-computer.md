```{seo}
:description: The supported OS for working with Duckietown is Ubuntu 22.04 or newer. Learn how to install Ubuntu on your computer, and what requirements it should have.
:keywords: computer setup, how to install ubuntu, duckietown supported OS, why ubuntu duckietown 
```

```{needget}
- A computer (laptop or desktop) satisfying [minimum requirements](setup-computer-requirements)
- A 32GB+ external drive (e.g., the Duckietown SD card + adapter)
---
- A computer with native Ubuntu installation
```

(setup-computer)=
# Setup - Computer

The first step in Duckietown is to [set up a computer appropriately](setup-install-ubuntu).

Duckietown is a platform designed to introduce learners to the tools and workflows of professional robotics. 

A critical skill and fundamental tool of every roboticist is the open source Linux operating system. In Duckietown, in particular, we use the Ubuntu distribution. 

## Why Ubuntu

For who has never had the experience, Ubuntu might be perceived as a barrier of entry to learning AI robotics, especially given the widespread distribution of other operating systems (Windows, macOS) in educational institutions.

We contend that using Ubuntu actually increases the accessibility to the science and technology of robot autonomy, for many more reasons than we will list here, but mainly because:

* it is **open source**, **free**, and **available worldwide**
* it is resource efficient, and runs comparatively well on inexpensive computers
* it is transparent - there is a file for everything
* it has a preexisting large community
* Ubuntu in particular has a UI that is very similar to standard Windows or macOS desktops

If you are concerned about using Ubuntu, it is good. You are here to learn and progress starts at the edge of our comfort zone. 

(setup-install-ubuntu)=
## Installing Ubuntu Desktop

Before installing Ubuntu:

1. Check if your computer will work well with it at [](setup-computer-requirements)
2. Decide if you will install Ubuntu as a dual boot - in which case ensure you have enough free space to make a partition.

```{tip}
We recommend installing Ubuntu as a dual boot when possible. Each time you turn on your computer, you will be able to choose which OS to run.
```

```{warning}
The currently supported version of Ubuntu is 22.04.x or newer.
```
 
To install Ubuntu, follow this [Ubuntu Desktop Installation Tutorial](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview).


## A note on other operating systems

Duckietown can work with other operating system such as Windows or macOS, but it will require extra work in addition to the instructions shown in this manual. 

The Duckietown staff is unfortunately able to provide help only for the officially supported OS. 

Q&As can be found in the [Duckietown archives](setup-account-stack-overflow)) and/or in the [Duckietown community on Slack](setup-account-slack). 

If you would like to document your solution, we will be glad to evaluate your PRs.

## A note on virtual machines

It is possible to run Ubuntu inside a virtual machine on both Windows and macOS hosts. 

Given the many possible combinations of virtual machines, OSs, and architectures, Duckietown staff will not be able to support you in case of need. Again, you can find hints and Q&As in the [Duckietown archives](setup-account-stack-overflow)) and/or in the [Duckietown community on Slack](setup-account-slack). 

(setup-computer-requirements)=
## Computer and internet requirements for using Duckietown

Depending on your use case (learner, instructor, developer), you will require a more resourceful machine to meet your Duckietown needs. 

### Required (learner):

* 60 GB of hard drive
* Quad-core 1.8GHz
* 4GB RAM
* GPU compatible with OpenGL 2.1+

### Recommended (instructor, developer): 

* 150 GB of hard drive
* Quad-core at 2.1Ghz, 
* 8GB RAM, 
* GPU compatible with OpenGL 2.1+
* [A computer model certified to work with Ubuntu](https://ubuntu.com/certified?q=&category=Laptop&category=Desktop&limit=20)