# Setup the Duckietown Shell

In this section, an application called `dts`, or the ***Duckietown Shell*** is setup.

It is a [command-line interface (CLI) prgram](https://en.wikipedia.org/wiki/Command-line_interface) which is used often with Duckietown operations, such as
* Updating a Duckiebot
* Driving a Duckiebot with a virtual keyboard
* Viewing the camera stream of a Duckiebot from a graphical app
* Using our MOOC exercise
* (and more!)


# `dts` versions and login's

Your `dts` is further setup in this section.

## Use the latest stable distribution version
```bash
dts --set-version daffy
```


## Set your Duckietown token
You could obtain your token by logging in on the [Duckietown homepage](https://duckietown.com). Then token looks like: `dt1-xxx`.

To add the token to `dts`, run the following command,
```bash
dts tok set YOUR_DUCKIETOWN_TOKEN
```

You can verify you successfully authenticated using the Duckietown token by running the command,
```bash
dts tok status
```

The expected output looks like the following,
```text
dts :  Correctly identified as uid = [YOUR_DUCKIETOWN_USER_ID]
```


## Configure Docker login
We leverage containerization a lot for reproducibility. Most procedures entail some `docker` operations behind the scene. That is why we setup the logins for docker within `dts`.

You will need:
* `YOUR_DOCKERHUB_USERNAME` (or login email address)
* `YOUR_DOCKERHUB_ACCESS_TOKEN` (to obtain one: [see this](https://docs.docker.com/docker-hub/access-tokens/))

```{attention}
* The credentials are only stored locally.
* They are stored in **plain text** at `~/.dt-shell/config.yaml`.
* Use an access token instead of your account password!
```  

You can pass wour DockerHub credentials to the Duckietown Shell by running the following command,
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
