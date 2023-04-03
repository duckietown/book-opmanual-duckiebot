## Step 2: Docker Account Setup

(dt-account-dockerhub)=
### DockerHub

Duckietown uses [DockerHub](https://hub.docker.com/duckietown) to distribute the containerized version 
of its software modules.

If you do not have one already,
you can sign up for a DockerHub account at [this link](https://hub.docker.com/signup).

You will need to note your username and password to use in the following setup steps.

### Configure Docker login

We leverage containerization a lot for reproducibility. Most procedures entail some `docker` operations behind the scene. That is why we need to begin by setting up the logins for docker within `dts`.

```{attention}
* The credentials are only stored locally.
* They are stored in **plain text** at `~/.dt-shell/config.yaml`.
* You can use an access token instead of your account password! (to obtain one: [see this](https://docs.docker.com/docker-hub/access-tokens/))
```  

You can pass your DockerHub credentials to the Duckietown Shell by running the following command,
```bash
dts config docker set \
    --username YOUR_DOCKERHUB_USERNAME \
    --password YOUR_DOCKERHUB_ACCESS_TOKEN
```

```{admonition} For developers
:class: dropdown

With an extra **positional** argument, one could specify a custom docker registry server other than 
`docker.io`. Check `dts config docker set --help` for more details.
```

Use the following to verify your input,
```bash
dts config docker info
```


## Verify everything is correct

Before we move on, let us make sure you have installed everything correctly.

If some of these commands don’t work, please go back and fix it before continuing.

If the Docker installation went well, then you can run the following command:

    $ docker run hello-world
    Hello from Docker!
    This message shows that your installation appears to be working correctly.

If you set up a Github account and private key, you should be able to run this command successfully:

    $ ssh -T git@github.com
    Hi GITHUB_USERNAME! You've successfully authenticated, but GitHub does not provide shell access.

If you have a valid DockerHub account then you can login as follows.

    $ docker login -u DOCKER_USERNAME
    Password:



## FAQs

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
