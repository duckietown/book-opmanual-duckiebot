## Step 2: Docker Installation

Duckietown uses [DockerHub](https://hub.docker.com/duckietown) to distribute the containerized version 
of its software modules, and most Duckietown procedures entail some `docker` operations behind the scenes. 

If you are unfamiliar with Docker, we strongly recommend reading the following reference page to gain a 
working understanding of this tool: [The Duckietown Intro to Docker](preliminaries-docker-basics)

`````{tab-set}

````{tab-item} Ubuntu

**1) Install Docker**

Install Docker by first ensuring that you don't have older versions of Docker on your system

    sudo apt-get remove docker docker-engine docker.io containerd runc
    
Then set up the apt repository containing Docker

    sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg
        
Add the official GPG key

    sudo mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    
And set up the repository with

    echo \
      "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
      "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Finally, update again and install Docker Engine and Docker Compose

    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    sudo apt-get install docker-compose

**2) Set up Docker**

Start by adding the user "docker" to your user group, then log out and back in

    sudo adduser `whoami` docker

```{attention}
You need to _log out and back in_ for this group change to take effect.
```

---

**Checkpoint ✅**

Now make sure that Docker was correctly installed by running the following tests

```{testexpect}
```bash
docker --version
docker buildx version
---
Make sure the Docker version is `v1.4.0+` and `buildx` version `v.0.8.0+`
```

```{testexpect}
Start the `hello-world` image with
```bash
docker run hello-world
---
You should see a message like `Hello from Docker!`
```

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

---

**Checkpoint ✅**

Now make sure that Docker was correctly installed by running the following test.

```{testexpect}
Start the `hello-world` image with
```bash
docker run hello-world
---
You should see a message like `Hello from Docker!`
```
````

````{tab-item} Windows (Beta)

**1) Install Docker**

Follow [these instructions](https://docs.docker.com/desktop/windows/wsl/) to install Docker on WSL.


---

**Checkpoint ✅**

Now make sure that Docker was correctly installed by running the following test.

```{testexpect}
Start the `hello-world` image with
```bash
docker run hello-world
---
You should see a message like `Hello from Docker!`
```

```{trouble}
I cannot start Docker from my WSL distribution.
---
Make sure you have WSL support for Docker enabled by following [these instructions](https://docs.docker.com/desktop/windows/wsl/#enabling-docker-support-in-wsl-2-distros).
```

````

`````
