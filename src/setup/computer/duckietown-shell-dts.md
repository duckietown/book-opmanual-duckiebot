(setup-dts)=
# The Duckietown Shell (`DTS`)

```{seo}
:description: How to install and set up DTS (Duckietown Shell), the terminal based and most powerful UI in Duckietown. 
:keywords: Duckietown, Duckiebot, DTS, Duckietown Shell, UI, terminal
```

This section describes how to install and set up `DTS` (`Duckietown Shell`).

```{needget}
Completed [](setup-computer-docker).
---
A computer with `DTS` installed and correctly set up.
```

## Introduction to `DTS`

`DTS` is a CLI (Command-Line Interface) program that is used for Duckietown-related operations.

## `DTS` Installation

To install `DTS`, run:

```shell
pipx install duckietown-shell
```

## Checkpoint 1

````{testexpect}
Run:

```shell
which dts
---
The path to `dts`.
````

## `DTS` Setup

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

### Docker Hub credentials

To set your Docker Hub credentials, run the following command, where `USERNAME` is your Docker Hub username and `PASSWORD` is a Docker Hub PAT (Personal Access Token):

```shell
dts config docker credentials set --username USERNAME --password PASSWORD
```

```{attention}
These credentials are **only stored locally**. **Never use your Docker Hub password** over a Docker Hub PAT.
```

## Checkpoint 2

````{testexpect}
Run:

```shell
dts config docker credentials info
---
The following output, where `USERNAME` is your Docker Hub username and `PASSWORD` is a partially hidden Docker Hub PAT:

```shell
Docker credentials:

        registry:   docker.io
        username:   USERNAME
        password:   PASSWORD

````
