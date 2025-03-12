(running-demos)=
# General Demo Running Procedure


This page describes the basic procedure for running demos. 
Some demos have specific requirements that must be adhered to, 
but the general process of running them through the Duckietown shell is standardized.

```{needget}
* A Duckiebot (configuration may depend on the demo) that is [initalized](setup-duckiebot-sd-card)
or a virtual robot
* Laptop configured, according to [](laptop-setup).
---
* A behavior executed on your Duckiebot or in the duckiematrix
```

##  DTProjects, Launchers and the `dts devel` API 

In general, code that runs on the robots is executed  is run in Duckietown as a 
[DTProject](book-devmanual-software:dtproject). You don't need all of the details for now but
those interested may want to refer to the [Software Developer Manual](book-devmanual-software:intro).

In summary, if you started from a [Coding project template](book-devmanual-software:project-templates), then
you can add your code in the `packages` directory and then add scripts to run your code 
in the `launchers` directory. 

Then you will want to build your code on your robot with:

```bash
dts devel build -H ![ROBOTNAME]
```

where you should replace `![ROBOTNAME]` with the name of your robot. As a result of the
build procedure you will see the list of launchers available. Then you can run your
a specific launcher named `![LAUNCHERNAME]` with 

```bash
dts devel run -H ![ROBOTNAME] -L ![LAUNCHERNAME]
```

```{tip}
The `dts devel` API has a lot more useful features that you can explore by looking
at the help files. E.g. 
    
    dts devel run --help

but don't worry if you don't understand what most of these options do at this point.
```

## Running Demos in the Duckiematrix

Typically demos can be run on a physical Duckiebot or in the 
[Duckiematrix](book-devmanual-duckiematrix:book). To do so, you will first need
to **create** a virtual robot:

```bash
dts duckiebot virtual create ![VIRTUAL_ROBOT_NAME]
```

and then **start** it:

```bash
dts duckiebot virtual start ![VIRTUAL_ROBOT_NAME]
``` 
 
Then after you run the duckiematrix (the map that 
you use should depend on the demo that you are trying to run), you will need to 
**attach** to it:

```bash
dts matrix attach ![VIRTUAL_ROBOT_NAME] ![ENTITY_NAME]
```

where `![VIRTUAL_ROBOT_NAME]` is a name you can choose and `![ENTITY_NAME]` 
is the name of the entity you want to connect to in the Duckiematrix. This
should be specified in the demo but a good guess is usually a good guess will
be `map_0/vehicle_0`. 

```{tip}
For more details please refer to the 
[Duckiematrix Manual](book-devmanual-duckiematrix:connecting-virtual-duckietown-robots-matrix).
```