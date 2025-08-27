(general-demo-procedure)=
# General Procedure for Running Demos

In general, any duckietown repository that has been built from one of the [templates](book-devmanual-software:project-templates).

In some cases, you may have an option to run the actual demo code on your *laptop* and communicate with the robot, or
to directly run the code on the *robot*. 

```{tip}
In most cases, you should try to run the code natively on the robot 
since this will be more *reproducible*. When you run the code on your laptop you will be connecting to the robot
through a wireless network which will induce a random latency and can cause unexpected or poor performance
```
In either case the first step will be to build the project image. To do so, enter the 
the repository containing the project code and run:

```commandline
dts devel build -H [!ROBOTNAME]
```
```{note}
To build the project on the laptop if you intend to run it from the laptop you can exclude the `-H [!ROBOTNAME]` - the 
default behaviour is to build the project on the machine where the `dts build` command is being run
```

```{note}
In some cases you may be able to skip the project building step if an image has already been pushed to the Docker 
registry. This should be specified inside the demo instructions. In this case, when you run the demo (next step)
the image will be *pulled* from the registry, which can take some time. 
```

Then you can run the demo with the command 

```commandline
dts devel run -H [!ROBOTNAME] -L [!LAUNCHER_NAME]
```

Again, this will run the code on the robot. If you would like to run the code on laptop you can switch the `-H`, which
specifies the *machine* to run the code on, with a `-R`, which specifies which *robot* to connect to. 

```{tip}
When you do `dts devel run` the code from your laptop will be copied to the robot with a command called 
[rsync](https://linux.die.net/man/1/rsync). This uses the same protocal as (SSH)[secure-shell]. As a result it 
will ask you for a password, which can get a annoying. It is recommended to avoid this by copying your SSH
credentials to the robot with:

    ssh-copy-id duckie@ROBOT_NAME.local

you will have ente your password to complete this but then you should never be asked for your password again. 
```

You may want to look at more of the details of the `dts devel` API for more advanced features.

```{todo}
where?
```