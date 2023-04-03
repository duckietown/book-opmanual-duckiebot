## Step 1: Dependency Installation

`````{tab-set}

````{tab-item} Ubuntu

**1) Install dependencies**

The basic development tools that you will need are `pip3`, `git`, `git-lfs`, `curl`, and `wget`.  Install these by running the 
following commands in the shell:

    sudo apt update
    sudo apt install -y python3-pip git git-lfs curl wget

```{attention}
If you are running Ubuntu on a virtual machine, install the package `open-vm-tools` in addition to the 
normal Ubuntu dependencies:

    sudo apt install open-vm-tools
```

**✅ Checkpoint**
```{todo}```

````

````{tab-item} MacOSX

**1) Install Git**

Most versions of MacOS will already have Git installed, and you can check that it is installed
by running the command `git version` in a terminal. 
However, if you don't have Git installed, you can follow 
[these instructions](https://github.com/git-guides/install-git#install-git-on-mac) 
to install it.

Follow 
[these instructions](https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage?platform=mac)
to install `git-lfs`.

**2) Install Quartz**

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

**✅ Checkpoint**
```{todo}```

````

`````