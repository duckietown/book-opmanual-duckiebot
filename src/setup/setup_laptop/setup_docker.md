## Step 2: Docker Installation

`````{tab-set}

````{tab-item} Ubuntu

**1) Install Docker**

Install Docker by following the instructions 
[here](https://docs.docker.com/install/linux/docker-ce/ubuntu/).

Adds user to "docker" group:

```shell
sudo adduser `whoami` docker
```

```{note}
You need to _log out and back in_ for the group change to take effect.
```

**2) Install Docker Compose**

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

**✅ Checkpoint**
```{todo}```

````

````{tab-item} MacOSX

**1) Install Docker**

Follow [these instructions](https://docs.docker.com/docker-for-mac/install/) to install Docker on MacOS.
Once done, follow the [post-install instructions](https://docs.docker.com/engine/install/linux-postinstall/)
to configure your Docker environment.

```{attention}
If you are using **Docker Desktop for Mac**, you will need to specify the amount of memory usable by Docker 
in order to run the Duckietown containers. Open the Docker menu and go to _Preferences_ then _Advanced_. 
Use the slider in the _Advanced_ tab to increase Memory to a minimum of `4.5GB`.
```

**✅ Checkpoint**
```{todo}```

````

`````