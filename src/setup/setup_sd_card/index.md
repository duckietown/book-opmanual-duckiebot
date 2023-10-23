(setup-duckiebot-sd-card)=
# Setup - Duckiebot SD Card

Here we will learn who to initialize an SD card with the Operating System that will run on the
Duckiebot on-board computer. This procedure is called `flashing`, or `burning` of the SD card.

```{needget}
- An SD card of size at least 32 GB
- At least 20 GB of free space on the computer
- An internet connection
- SD card reader
- Duckietown Shell, as configured in [](laptop-setup-shell).
- Docker, as configured in [](laptop-setup-docker).
- Duckietown Token, as configured in [](dt-account).
- 30 minutes on average (depends on internet connection and SD card adapter used)
---
A flashed Duckiebot SD card, ready to be used to give life to your Duckiebot.
```


```{admonition} For non-Unix-like systems
:class: dropdown

Though the suggested operating system for this operation is Ubuntu, this
should work on any Unix-like operating system. If you are using dts through `WSL` or experience
any issues while performing this procedure, when prompted to enter the device name, simply
provide a path to a file, for example `/home/user/duckiebot_sd_card.img`. The program will
proceed by creating a disk image in that file instead. You can later transfer it to an SD card
using any standard flashing tool, e.g., `etcher`, `dd`.
```


```{note}
If you are using a microSD to SD card adapter, make sure the adapter does not have the 
write protection enabled. Check 
[this link](https://kb.sandisk.com/app/answers/detail/a_id/1102/~/sd%2Fsdhc%2Fsdxc-memory-card-is-write-protected-or-locked)
to learn more.
```


(chose-robot-hostname)=
## Step 1) Choose a name for your robot

Pick a `hostname` for your robot. This will be the name of your robot and has to be unique within
a fleet of robots connected to the same network.
A valid `hostname` satisfies all the following requirements:

- it is lowercase
- it starts with a letter
- it contains only letters, numbers, and underscores


## Step 2) Burn the SD card

There are two interfaces to the process of burning a Duckiebot SD card:

 - GUI: A graphical wizard-like interface;
 - CLI: A terminal-based command line interface (for those who crave the terminal experience);

Choose the interface that best fits your preferences and skip the other.


``````{grid} 2
`````{grid-item-card}  GUI - Graphical wizard
````{href} ./gui.html
```{rawimage} ../../_images/init-sd-card-gui-icon.png
:width: 85%
:align: center
```
````
`````

`````{grid-item-card}  CLI - Command line
````{href} ./cli.html
```{rawimage} ../../_images/init-sd-card-cli-icon.png
:width: 80%
:align: center
```
````
`````
``````
