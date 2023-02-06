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


```bash
dts config docker \
    --docker-username YOUR_DOCKERHUB_USERNAME \
    --docker-password YOUR_DOCKERHUB_ACCESS_TOKEN
```

To verify:
```bash
dts challenges info

# (The following line is expected among the output)
# credentials_available: [docker.io]
```

:::{admonition} For developers
:class: dropdown

Use the extra option `--docker-registry` to specify a custom docker registry other than `docker.io`
:::