## Step 2: Docker Account Setup

Duckietown leverages containerization to ensure software portability and reproducibility.
Most procedures entail the use of `docker` operations behind the scene.
That is why we need to set up the logins for docker within `dts`.

We use [DockerHub](https://hub.docker.com/duckietown) to distribute the containerized version 
of its software modules, and most Duckietown procedures entail some `docker` operations behind the scenes. 

If you are unfamiliar with Docker, we strongly recommend reading the following reference page to gain a 
working understanding of this tool: [The Duckietown Intro to Docker](preliminaries-docker-basics)


(dt-account-dockerhub)=
### 1) Create a DockerHub account

If you do not have one already,
you can sign up for a DockerHub account at [this link](https://hub.docker.com/signup).

(dt-account-dockerhub-make-access-token)=
#### Make an access token

Follow the instructions on [this page](https://docs.docker.com/docker-hub/access-tokens/)
to create a new personal access token on DockerHub.


(dt-account-dockerhub-login)=
### 2) Log in to Docker

Once you have an account on DockerHub and an access token, you can test them by logging in using the command,

    docker login -u DOCKER_USERNAME

where `DOCKER_USERNAME` is the username you chose when signing up on DockerHub. 
You will then be prompted for your password, paste the access token we created earlier and press 
<kbd>Enter</kbd>.


(dt-account-dockerhub-config-docker-set)=
### 3) Configure shell

We are now going to provide the same username and access token to the shell in order to automate
most of the back-end operations involving docker.

```{attention}
* These credentials are **only stored locally**;
* **Never use your account password** instead of an access token;
```  

You can pass wour DockerHub credentials to the Duckietown Shell by running the following command,
```bash
dts config docker credentials set \
    --username DOCKERHUB_USERNAME \
    --password DOCKERHUB_ACCESS_TOKEN
```

```{admonition} For developers
:class: dropdown

With an extra **positional** argument, one could specify a custom docker registry server other than 
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
  join the Duckietown community on StackOverflow and Slack following the instructions below and search 
  for previous solutions.

You can join the 
[Duckietown community on Slack at this link](https://duckietown.com/join-slack). 

There you can request an invitation to the [Duckietown Stack Overflow](https://stackoverflow.com/c/duckietown/questions), in particular, following [these instructions](https://duckietown.slack.com/archives/CHHQJ0E0H/p1670874390660429).

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
