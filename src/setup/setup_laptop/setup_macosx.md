(laptop-setup-mac)=
# Setup for MacOS


```{warning}
This configuration is not officially supported. We recommend using the Ubuntu Operating System for an 
optimal experience.
```


(laptop-setup-mac-basic)=
## Basic dependencies

Most versions of MacOS will already have Git installed, and you can check that it is installed
by running the command `git version` in a terminal. 
However, if you don't have Git installed, you can follow 
[these instructions](https://github.com/git-guides/install-git#install-git-on-mac) 
to install it.

Follow 
[these instructions](https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage?platform=mac)
to install `git-lfs`.


(laptop-setup-mac-quartz)=
## Quartz 

You will also need the latest version of `XQuartz`.

You can install it using `brew`,

    brew install xquartz

Or, download it from [here](https://www.xquartz.org/) and follow the instructions.

After installing `XQuartz`, run it by executing the command,

    open -a XQuartz

Go to "Preferences" and in the "Security" tab make sure that the checkbox next to 
"Allow connections from network clients" is ticked. You can now close `XQuartz`.

You may want to add the following lines to your `.bashrc` file. If you are using `zsh`, add these to your `.zshrc` file instead.

    export IP=$(ifconfig en0 | grep inet | awk '$1=="inet" {print $2}')
    xhost +$IP

These will find your IP and then allow incoming connections to it in order to be able to 
popup windows from within docker containers.

Alternatively, if you do not wish to make these changes permanent, you can run the commands above 
every time you open a new terminal.

```{trouble}
The command `xhost` is not found.
---
Add the path `/usr/X11/bin` to your `PATH` variable. e.g., `PATH=/usr/X11/bin:${PATH} xhost ...`.
```


(laptop-setup-mac-docker)=
## Docker

Follow [these instructions](https://docs.docker.com/docker-for-mac/install/) to install Docker on MacOS.
Once done, follow the [post-install instructions](https://docs.docker.com/engine/install/linux-postinstall/)
to configure your Docker environment.

```{attention}
If you are using **Docker Desktop for Mac**, you will need to specify the amount of memory usable by Docker 
in order to run the Duckietown containers. Open the Docker menu and go to _Preferences_ then _Advanced_. 
Use the slider in the _Advanced_ tab to increase Memory to a minimum of `4.5GB`.
```


(laptop-setup-mac-shell)=
## Duckietown Shell

Install the Duckietown Shell using the following command,

```shell
pip3 install --no-cache-dir --user --upgrade duckietown-shell
```

Then, make sure your system is able to find local binaries by adding the following to your `.bashrc` file. 

```{attention}
Again, if you are using `zsh`, replace the `.bashrc` in the commands below with `.zshrc` instead.
```

    export PATH=~/.local/bin:${PATH}

Then source the updates to your current shell

```{shell}
source ~/.bashrc
```

You can now check that `dts` was installed with 

```{shell}
which dts
```

The first thing you need to do with the Duckietown Shell is to set the Duckietown software
distribution you want to work with. For this version of the book, we use `daffy`.
Set the shell to use the `daffy` distribution by running the following command,

```shell
dts --set-version daffy
```
