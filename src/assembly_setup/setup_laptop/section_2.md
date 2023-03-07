# `dts` versions and login's

Your `dts` is further setup in this section.

## Use the latest stable distribution version
```bash
dts --set-version daffy
```

## Set your Duckietown token
You could obtain your token by logging in on the [Duckietown homepage](https://duckietown.com). Then token looks like: `dt1-xxx`.

To add the token to `dts`:
```bash
dts tok set YOUR_DUCKIETOWN_TOKEN
```

To verify:
```bash
dts tok status

# (expected outcome)
# dts :  Correctly identified as uid = [YOUR_DUCKIETOWN_USER_ID]
```

## Configure Docker login
We leverage containerization a lot for reproducibility. Most procedures entail some `docker` operations behind the scene. That is why we setup the logins for docker within `dts`.

You will need:
* `YOUR_DOCKERHUB_USERNAME` (or login email address)
* `YOUR_DOCKERHUB_ACCESS_TOKEN` (to obtain one: [see this](https://docs.docker.com/docker-hub/access-tokens/))

:::{attention}
* The credentials are only stored locally.
* They are stored in **plain text** at `~/.dt-shell/config.yaml`.
* Use an access token instead of your account password!
:::


### To set docker credentials
```bash
dts config docker set \
    --username YOUR_DOCKERHUB_USERNAME \
    --password YOUR_DOCKERHUB_ACCESS_TOKEN
```

:::{admonition} For developers
:class: dropdown

With an extra **positional** argument, one could specify a custom docker registry server other than `docker.io`. Check `dts config docker set --help` for more details.
:::

### To verify existing docker credentials
```bash
dts config docker info

# expected outcome:
# saved docker registry server (default: docker.io) and the username
```

### FAQs
```{trouble}
I mistakenly set a wrong/unwanted username or password. How can I update the credentials?
---
Just run the command again with the correct credentials. Only the latest inputs are stored for the same docker registry.
```

:::{trouble}
I would like to remove my stored docker credentials. How could I achieve that?
---
Simply use a text editor to remove the section `docker-credentials` in `~/.dt-shell/config.yaml` file.
:::