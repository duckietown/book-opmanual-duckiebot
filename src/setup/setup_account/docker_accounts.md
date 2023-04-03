## Step 2: Docker Account Setup

Duckietown uses [DockerHub](https://hub.docker.com/duckietown) to distribute the containerized version 
of its software modules, and most Duckietown procedures entail some `docker` operations behind the scenes. 

If you are unfamiliar with Docker, we strongly recommend reading the following reference page to gain a 
working understanding of this tool: [The Duckietown Intro to Docker](preliminaries-docker-basics)

(dt-account-dockerhub)=
### 1) Create a DockerHub account

If you do not have one already,
you can sign up for a DockerHub account at [this link](https://hub.docker.com/signup).

You will need to note your username and password to use in the following setup steps.

### 2) Log in to Docker

If you have a valid DockerHub account then you can log in as follows

    docker login -u DOCKER_USERNAME

You will then be prompted for your password.

### 3) Configure Docker login with `dts`

We leverage containerization for reproducibility. Most Duckietown procedures entail some `docker` operations behind the scenes. That is why we need to begin by setting up the logins for docker within `dts`.

```{attention}
* The credentials are only stored locally.
* They are stored in **plain text** at `~/.dt-shell/config.yaml`.
* You can use an access token instead of your account password! (to obtain one: [see this](https://docs.docker.com/docker-hub/access-tokens/))
```  

You can pass your DockerHub credentials to the Duckietown Shell by running the following command,

```bash
dts config docker set \
    --username YOUR_DOCKERHUB_USERNAME \
    --password YOUR_DOCKERHUB_PASSWORD_OR_ACCESS_TOKEN
```

Be sure to replace `YOUR_DOCKERHUB_USERNAME` and `YOUR_DOCKERHUB_PASSWORD_OR_ACCESS_TOKEN` with your credentials.

```{admonition} For developers
:class: dropdown

With an extra **positional** argument, one could specify a custom docker registry server other than 
`docker.io`. Check `dts config docker set --help` for more details.
```

### 4) Configure Docker with the Challenges Server

The [Duckietown Challenges Server](https://challenges.duckietown.org) allows you to participate in robotics
competitions, evaluate your work on the cloud, submit learning experiences, etc., by uploading your work, packaged as a Docker image, to DockerHub.

Use the following command to update your credentials

    dts challenges config --docker-username USERNAME --docker-password PASSWORD

where, `USERNAME` and `PASSWORD` need to be replaced with your DockerHub credentials.

---

### Checkpoint ✅

Before we move on, let us make sure you have installed everything correctly. 

```{tip}
Remember, never skip a checkpoint! If you have trouble with any of these commands, see the troubleshooting section below.
```

If your Docker login was successful, you should be able to run

    docker system info | grep "Username"

to see your DockerHub username.

```{admonition} For developers
:class: dropdown
The `| grep "Username"` portion of this command finds only the output line that matches "Username".  You can see your entire Docker system configuration by running the command `docker system info`.
```

You can verify your Docker login configuration with `dts` by first installing the `dts config` tool and then using it to show your Docker info.
    
    dts install config
    dts config docker info

If you've set your token and updated your credentials for the challenges server, you can run

    dts challenges info

To see the following message

```
    ~        You are successfully authenticated:
    ~
    ~                     ID: YOUR ID
    ~                   name: YOUR NAME
    ~                  login: YOUR DUCKIETOWN ACCOUNT 
    ~
    ~         You can find the list of your submissions at the page:
    ~
    ~              https://challenges.duckietown.org/v4/humans/users/YOUR ID
```

### Troubleshooting

If you continue past a test that did not work, you will have further software issues down the line, and they will be more complex to fix. Instead, if you do not get the expected outcome at any checkpoint:

* First check the troubleshooting guide below.
* If you run into any issues that can't be solved using the troubleshooting section, join the Duckietown community on StackOverflow and Slack following the instructions below and search for previous solutions.

You can join the 
[Duckietown community on Slack at this link](https://join.slack.com/t/duckietown/shared_invite/enQtNTU0Njk4NzU2NTY1LWM2YzdlNmJmOTg4MzAyODc2YTI3YTc5MzE2MThkZGUwYTFkZWQ4M2ZlZGU1YTZhYjg5YTgzNDkyMzI2ZjNhZWE). 
There you can request an invitation to the Duckietown Stack Overflow team.

```{trouble}
I mistakenly set a wrong/unwanted username or password. How can I update the credentials?
---
Just run the command again with the correct credentials. 
Only the latest inputs are stored for the same docker registry.
```

```{trouble}
I would like to remove my stored docker credentials. How could I achieve that?
---
Simply use a text editor to remove the section `docker-credentials` in `~/.dt-shell/config.yaml` file.
```
