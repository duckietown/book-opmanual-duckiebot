# Dependencies

```{seo}
:description: How to install some of the dependencies necessary to interact with your Duckiebot.
:keywords: Duckietown, Duckiebot, dependencies
```

This section describes how to install some of the dependencies necessary to interact with your Duckiebot.

```{needget}
Completed [](intro.md).
---
A computer with some of the dependencies necessary to interact with your Duckiebot installed.
```

## Installation

To install some of the dependencies necessary to interact with your Duckiebot, run:

```shell
sudo apt update
sudo apt install -y ca-certificates curl git git-lfs gnupg libfuse2 pipx
pipx ensurepath
```

````{note}
If you are running Ubuntu in a VM, run the following command as well:

```shell
sudo apt install open-vm-tools
```
````

## Checkpoint

```{testexpect}
Run:

```shell
pipx --version
---
The version number for `pipx`.
```

```{note}
If a test fails:
1. Try following the instructions again.
2. Check for a troubleshooting section at the bottom of the page.
3. Join the [Duckietown community on Slack](https://duckietown.com/join-slack), where you can request an invitation to the [Duckietown Stack Overflow team](https://stackoverflowteams.com/c/duckietown), and search for previous solutions.
```
