(setup-dts)=
# Duckietown Shell (`dts`) installation

```{seo}
:description: How to install and set up DTS (Duckietown Shell), the terminal based and most powerful UI in Duckietown. 
:keywords: Duckietown, Duckiebot, DTS, Duckietown Shell, UI, terminal
```

This section describes how to install and set up `DTS` (`Duckietown Shell`), a CLI (Command-Line Interface) program that is used for Duckietown-related operations.

```{needget}
- [Docker is installed and set up](setup-sw-docker)
- [GitHub is installed and set up](setup-sw-github)
- [Duckietown account](setup-account-duckietown-hub)
---
- A computer with `DTS` installed and correctly set up.
```

## `dts` Installation

To install `dts`, run:

```shell
pipx install duckietown-shell
```

### Checkpoint 1 ✅

To verify that `dts` has been installed correctly:

````{testexpect}
Run:

```shell
which dts
---
The path to `dts`.
````

## `dts` Setup

To appropriately configure the Duckietown Shell:

1. [Login `dts` as a Duckietown User](dt-account-set-token)
2. [Provide DockerHub credentials](dt-account-dockerhub-config-docker-set)

(dt-account-set-token)=
### Configure the Duckietown token in the Duckietown Shell

To perform the initial setup of `DTS`:

1. Run `dts`.
2. Select `ente` using <kbd>UpArrow</kbd> and <kbd>DownArrow</kbd>.
3. Press <kbd>Enter</kbd>.
4. Copy your [Duckietown Token](https://hub.duckietown.com/token).
5. Paste your Duckietown Token into the terminal.
6. Press <kbd>Enter</kbd>.

````{note}
The resulting output should look like the following, where `UID` is your Duckietown UID (User ID):

```shell
dts :  Correctly identified as uid = UID
```
````

````{note}
To switch your `DTS` profile from `daffy` to `ente`, run:

```shell
dts profile switch ente
```
````

You can change the token/login as a different user with:

    dts tok set

and verify it with:

    dts tok status



(dt-account-dockerhub-config-docker-set)=
### Configure Docker in the Duckietown Shell

We are now going to provide the same username and access token to the shell to automate
most of the back-end operations involving Docker.

```{attention}
* These credentials are **only stored locally**;
* **Never use your account password** instead of an personal access tokens (PAT);
```  

Recall your `DOCKERHUB_USERNAME` from [](dt-account-dockerhub) and create a PAT following [DockerHub instructions on access tokens](https://docs.docker.com/security/access-tokens/).

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

<!--
(dt-account-dockerhub-shell-credentials)=
### 1) Configure the Duckietown Shell

The first thing you need to do with `dts` is to set the Duckietown software distribution you want to work with.
For this version of the book, we use daffy. Set the shell to use a profile on the daffy distribution by running the command

    dts profile switch daffy

(dt-account-register)=
### 2) Get a Duckietown Token

Now your Duckietown Shell needs a Duckietown token. The Duckietown Token allows you to authenticate yourself and your robots against the Duckietown network.

You can make a Duckietown account for free from the Duckietown Hub.
[Make an account here.](https://hub.duckietown.com/signup/)

The token is a string of letters and numbers that looks something like this:

    dt1-7vEuJsaxeXXXXX-43dzqWFnWd8KBa1yev1g3UKnzVxZkkTbfSJnxzuJjWaANeMf4y6XSXBWTpJ7vWXXXX

To find your token, first [log in](https://hub.duckietown.com/signin/) to your account, 
then open [the profile page](https://hub.duckietown.com/profile/) in your browser:

Copy your token to use in the next step.
-->

### Troubleshooting

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