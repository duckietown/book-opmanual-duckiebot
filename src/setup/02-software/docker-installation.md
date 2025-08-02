(setup-sw-docker)=
# Setup - Docker

```{seo}
:description: How to install and set up Docker on your computer. This is a necessary step to use Duckietown software. 
:keywords: Duckietown, Duckiebot, Docker, computer setup
```

This section describes how to install and set up Docker on your computer.

```{needget}
Completed [](setup-computer-dependencies-installation).
---
A computer with Docker installed and set up.
```

## Installation

If you have prior installations of Docker, start by cleaning up. To remove older versions of Docker, run:

```shell
sudo apt remove containerd docker docker-engine docker.io runc
```

To add the official GPG (GNU Privacy Guard) key and set up the repository, run:

```shell
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

To install Docker Engine and Docker Compose, run:

```shell
sudo apt update
sudo apt install containerd.io docker-buildx-plugin docker-ce docker-ce-cli docker-compose docker-compose-plugin
```

## Docker Setup

```{warning}
Make sure not to skip this part, it is a common source of troubles.
```

To add `docker` to your user group, run:

```shell
sudo adduser `whoami` docker
sudo reboot
```

To log into Docker Hub, run the following command, where `USERNAME` is your Docker Hub username:

```shell
docker login -u USERNAME
```

## Checkpoint

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
If you are unfamiliar with Docker, we strongly recommend reading the following reference page to gain a 
working understanding of this tool: [The Duckietown Intro to Docker](preliminaries-docker-basics)
```

--------- DOCKER SETUP WITH DTS


(dt-account-dockerhub-make-access-token)=
### Make an access token

Follow the instructions on [this page](https://docs.docker.com/docker-hub/access-tokens/)
to create a new personal access token on DockerHub.



(dt-account-dockerhub-login)=
### 2) Log in to Docker

Once you have an account on DockerHub and an access token, you can test them by logging in using the command,

    docker login -u DOCKER_USERNAME

where `DOCKER_USERNAME` is the username you used when signing up for DockerHub. 
You will then be prompted for your password, paste the access token we created earlier, and press 
<kbd>Enter</kbd>.


(dt-account-dockerhub-config-docker-set)=
### 3) Configure shell

We are now going to provide the same username and access token to the shell to automate
most of the back-end operations involving Docker.

```{attention}
* These credentials are **only stored locally**;
* **Never use your account password** instead of an access token;
```  

You can pass your DockerHub credentials to the Duckietown Shell by running the following command,
```bash
dts config docker credentials set --username DOCKERHUB_USERNAME --password DOCKERHUB_ACCESS_TOKEN
```

```{admonition} For developers
:class: dropdown

With an extra **positional** argument, one could specify a custom Docker registry server other than 
`docker.io`. Check `dts config docker set --help` for more details.
```

---

### Checkpoint ✅

Before we move on, let us make sure you have set our credentials correctly.

```{tip}
Never skip a checkpoint!\
If you have trouble with any of these commands, see the FAQs section below.
```

````{testexpect}
If your Docker login was successful, you should be able to run
```bash
dts config docker credentials info
---
You should see an output similar to the following,

```bash
Docker credentials:
. registry:   docker.io
. username:   DOCKERHUB_USERNAME
. secret:   DOCKERHUB_ACCESS_TOKEN
````

### FAQs

If you continue past a test that did not work, you will have further software issues down the line, 
and they will be more complex to fix. Instead, if you do not get the expected outcome at any checkpoint:

* First check the troubleshooting guide below.
* If you run into any issues that can't be solved using the troubleshooting section, 
  join the Duckietown community on StackOverflow and Slack, following the instructions below, and search 
  for previous solutions.

You can join the 
[Duckietown community on Slack at this link](https://duckietown.com/join-slack). 

There you can request an invitation to the [Duckietown Stack Overflow](https://stackoverflow.com/c/duckietown/questions), in particular, following [these instructions](https://duckietown.slack.com/archives/CHHQJ0E0H/p1670874390660429).

```{trouble}
I mistakenly set a wrong/unwanted username or password. How can I update the credentials?
---
Just run the command again with the correct credentials. 
Only the latest inputs are stored for the same Docker registry.
```

```{trouble}
I would like to remove my stored Docker credentials. How could I achieve that?
---
Simply use a text editor to remove the section `docker-credentials` in `~/.dt-shell/config.yaml` file.
```