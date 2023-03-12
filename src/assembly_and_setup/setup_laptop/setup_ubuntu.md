# Setup for Ubuntu

Duckietown officially supports Ubuntu 20.04 and Ubuntu 22.04.

```{note}
Having Ubuntu is not an enforced requirement, and everything should in theory work on any 
Linux operating system. Please, be aware that using an operating system that is not 
officially supported reduces the ability of the Duckietown team and the whole community 
to provide technical support when needed.
```


(laptop-setup-ubuntu-system)=
## System installation 

```{note}
While you can install Ubuntu in a virtual machine, 
if you have a physical Duckietown robot, you must install Ubuntu natively.
```

Install the Ubuntu operating system. Ubuntu 22.04 is strongly suggested.

Follow the 
[official documentation](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop)
about how to install Ubuntu.


(laptop-setup-ubuntu-basic)=
## Basic dependencies 

Installs pip3, git, git-lfs, curl, wget:

```shell
sudo apt update
sudo apt install -y python3-pip git git-lfs curl wget
```


(laptop-setup-ubuntu-docker)=
## Docker 

Install Docker by following the instructions 
[here](https://docs.docker.com/install/linux/docker-ce/ubuntu/).

Adds user to "docker" group:

```shell
sudo adduser `whoami` docker
```

```{note}
You need to _log out and back in_ for the group change to take effect.
```

Make sure you have docker-compose installed:

```shell
sudo apt-get install docker-compose
```

Make sure the Docker version is `v.0.8.0+` and `buildx` version `v1.4.0+` through:

```shell 
docker --version
docker buildx --version
```

```{warning}
If you missed this step, you will later run into docker permission issues.
```


(laptop-setup-ubuntu-shell)=
## Duckietown Shell

Install the Duckietown Shell using the following command,

```shell
pip3 install --no-cache-dir --user --upgrade duckietown-shell
```

The first thing you need to do with the Duckietown Shell, is set the Duckietown software
distribution you want to work with, for this version of the book, we use `daffy`.
Set the shell to use the `daffy` distribution by running the following command,

```shell
dts --set-version daffy
```


## For virtual machines

For VMWare, install the package `open-vm-tools`:

 ```shell
 sudo apt install open-vm-tools
```