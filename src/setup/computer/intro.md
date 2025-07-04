```{seo}
:description: How to set up your computer to interact with your Duckiebot.
:keywords: Duckietown, Duckiebot, computer
```

(computer)=
# Computer

This chapter describes how to set up your computer to interact with your Duckiebot.

```{needget}
* A computer with at least `50 GB` of free space running [Ubuntu 20.04 or newer](https://ubuntu.com/tutorials/install-ubuntu-desktop).
* An Internet connection.
* A [GitHub account](https://github.com/join).
* An [SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
* A [Duckietown account](https://hub.duckietown.com/signup/).
* A [Docker Hub account](https://hub.docker.com/signup).
---
A computer set up to interact with your Duckiebot.
```

```{attention}
Throughout this book, replace `DUCKIEBOT_NAME` with your Duckiebot's `hostname`, which does not include `.local` at the end.
```

```{note}
<kbd>Key</kbd> indicates a keyboard key.
```

## Native installation vs VM

Running Ubuntu natively is recommended but not strictly required.
If you are running Ubuntu in a VM (Virtual Machine), make sure that you are using a bridged network adapter (e.g., VirtualBox uses NAT by default), which will allow you to be on the same subnetwork as your Duckiebot.

```{note}
When running a VMware machine on a macOS host, it may be necessary to have the following network adapters:
* `Share with my Mac` (for connecting to the Internet).
* `Bridged Networking` (for connecting to your Duckiebot).
```
