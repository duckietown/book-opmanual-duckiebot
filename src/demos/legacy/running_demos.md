(running-demos)=
# General Demo Running Procedure

```{todo}
AfD review
```

This page describes the basic procedure for running demos. Some demos have specific requirements that must be adhered to, but the general process of running them through the Duckietown shell is standardized.

```{needget}
* A Duckiebot in `DB18` configuration that is [initalized](setup-duckiebot-sd-card)
* Laptop configured, according to [](#laptop-setup).
---
* A behavior executed on your Duckiebot.
```

<!--
<div class='requirements' markdown='1'>

Requires: A Duckiebot in `DB18` configuration that is [initalized](setup-duckiebot-sd-card)

Requires: Laptop configured, according to [](#laptop-setup).

Requires: Other requirements are demo specific, see the specific pages

</div>
-->

## Start demos
In the [Duckietown dt-core](https://github.com/duckietown/dt-core/tree/daffy/packages), some ROS packages serve as building blocks for complex demos. Each package contains node-specific launch files. The `duckietown_demos` package contains demo launch files that combine multiple node launch files and adds the necessary connections to stage demos that use dozens of nodes.

The launch procedure for both types is very similar. The generic command is:

    dts duckiebot demo --duckiebot_name ![DUCKIEBOT_NAME] --demo_name ![DEMO_NAME] --package_name ![PACKAGE_NAME] --image duckietown/![IMAGE]:daffy
    
This command will start the `DEMO_NAME.launch` launch file in the `PACKAGE_NAME` package from the `duckietown/![IMAGE]:daffy` Docker image on the `DUCKIEBOT_NAME` Duckiebot.
 
Note: Currently `daffy` is the development branch and the `dts` commands work by default with the `master19` version. That is why you should __always__ specify the image with the `daffy` tag!

You can find the specific command for each demo in the corresponding part of the book. 


## Debug options
You can open a terminal in the container running the demo you want by appending the option `--debug` to the command. An example is:

    dts duckiebot demo --duckiebot_name ![DUCKIEBOT_NAME] --demo_name ![DEMO_NAME] --package_name ![PACKAGE_NAME] --image duckietown/![IMAGE]:daffy --debug

This enables you to access to the `ROS` debug informations of the nodes that are launched. This is the same output that you can see in the `logs` window of the particular container on Portainer.
