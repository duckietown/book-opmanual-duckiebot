(setup-sw-dependencies-installation)=
# Software dependencies installation

```{seo}
:description: Learn how to install the software dependencies necessary to work with Duckietown. 
:keywords: Duckietown, Duckiebot, dependencies, computer setup
```

This section describes how to install the dependencies necessary to use Duckietown, in particular Duckiebots.

```{needget}
- Completed [Computer OS setup](setup-computer)
- Completed [Accounts setup](dt-account)
---
A computer with the dependencies necessary to interact with Duckietown.
```

## Dependencies Installation

Open a terminal and run, in order:

```shell
sudo apt update
sudo apt install -y ca-certificates curl git git-lfs git-extras gnupg libfuse2 pipx
pipx ensurepath
```

````{note}
If you are running Ubuntu in a VM, in addition:

```shell
sudo apt install open-vm-tools
```
````

## Checkpoint

```{warning}
Never skip a checkpoint! If checkpoints fail (for whatever reason), chances are future steps will not work either. [Seek help](https://duckietown.com/contact/) if needed. 
```

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
