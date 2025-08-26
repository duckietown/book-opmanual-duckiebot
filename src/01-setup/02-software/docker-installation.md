(setup-sw-docker)=
# Docker installation

```{seo}
:description: How to install and set up Docker on your computer. This is a necessary step to use Duckietown software. 
:keywords: Duckietown, Duckiebot, Docker, computer setup
```

This section describes how to install and set up Docker on your computer.

```{needget}
Completed [](setup-sw-dependencies-installation).
---
A computer with Docker installed and correctly set up.
```

## Remove previous installations

If you have prior installations of Docker, start by cleaning up. To remove older versions (open a terminal and) run:

```shell
sudo apt remove containerd docker docker-engine docker.io runc
```

## Docker Engine and Docker Compose installation

To add the official GPG (GNU Privacy Guard) key and set up the repository, run:

```shell
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Then install Docker Engine and Docker Compose, by running:

```shell
sudo apt update
sudo apt install containerd.io docker-buildx-plugin docker-ce docker-ce-cli docker-compose docker-compose-plugin
```

## Docker Setup

```{warning}
**Do not skip this part**, it is a common source of troubles.
```

To prevent permission/access errors, add `docker` to your user group:

```shell
sudo adduser `whoami` docker
sudo reboot # this will reboot your device
```

(dt-account-dockerhub-make-access-token)=
### Make an access token

We will need to provide login credentials to Docker Hub.

First, [create a new personal access token](https://docs.docker.com/docker-hub/access-tokens/) on DockerHub.

Then,

```shell
docker login -u DOCKERHUB_USERNAME
```

Where `DOCKERHUB_USERNAME` is your Docker Hub username, created during [](setup-account-docker). You will then be prompted for your password, paste the access token we created earlier, and press 
<kbd>Enter</kbd>.


## Checkpoint

To make sure the installation was completed successfully:

```{testexpect}
Run:

```shell
docker --version
---
The version number for `docker`.
```

```{testexpect}
Run:

```shell
docker buildx version
---
The version number for `buildx`.
```

```{testexpect}
Run:

```shell
docker run hello-world
---
```shell
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```


```{seealso}
If you are unfamiliar with Docker, we strongly recommend reading the following reference page to gain a working understanding of this tool: [The Duckietown Intro to Docker](preliminaries-docker-basics)
```

