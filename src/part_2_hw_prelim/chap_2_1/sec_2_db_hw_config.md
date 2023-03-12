(duckiebot-configurations)= 
# Duckiebot Configurations

```{needget}
* Nothing
---
* Knowledge of Duckiebot configuration naming conventions and their respective functionalities.
```

We define the different Duckiebot configurations, from the first `DB17` used during the MIT course 2.166 in 2017 to the latest available.  

Duckiebots `DB18` onwards can be obtained from the [Duckietown project store](https://cutt.ly/u81K1MU). 

(duckiebot-configurations-overview)= 
## Overview

| Model |  Computation  |              Sensing|             Actuation| Memory |       Power |       Notes   |
|-------|:-------------:|:--------------------------------:|:---------------------------------:|:------:|:-----------------:|:----------------:|
| [DB17](#duckiebot-config-db17)   	|      RPI3     	|              Camera              	|     2x DC motors, 5x RGB LEDs     	|  32GB  	|   Off-the-shelf   	|                  	|
| [DB18](#duckiebot-config-db18)   	|     RPI3B+    	|              Camera              	|     2x DC motors, 5x RGB LEDs     	|  32GB  	| [Duckie-power bank]({#db-opmanual-dtbattery-v1}) 	| addressable LEDs 	|
| [DB19](#duckiebot-config-db19)   	|     RPI3B+    	|      Camera, Wheel Encoders      	|     2x DC motors, 5x RGB LEDs     	|  32GB  	| [Duckie-power bank]({#db-opmanual-dtbattery-v1}) 	|                  	|
| [DB21M](#duckiebot-config-db21m) 	|     JN2GB     	| Camera, Wheel Encoders, ToF, IMU 	| 2x DC motors, 4x RGB LEDs, Screen 	|  32GB  	|   [Duckiebattery]({#db-opmanual-dtbattery-v2})    	|    Chassis v1    	|
| [DB21](#duckiebot-config-db21)  	| JN2GB / JN4GB 	| Camera, Wheel Encoders, ToF, IMU 	| 2x DC motors, 4x RGB LEDs, Screen 	|  64GB  	|   [Duckiebattery]({#db-opmanual-dtbattery-v2})   	|    Chassis v2    	|

Legend:

- "JN": NVIDIA Jetson Nano
- "RPI": Raspberry Pi
- "ToF": Time of flight
- "IMU": Inertial Measurement Unit (Accelerometer, Gyroscope)

(duckiebot-config-db21)=
## Duckiebot version 2021, or `DB21`

The Duckiebot `DB21` debuted with the "[Self-Driving Cars with Duckietown](https://www.duckietown.org/mooc)" massive open online course, as version [`DB21M`](#duckiebot-config-db21m).


Later revisions, referred to under the broader label `DB21` and then just ` DB-J`, improve the `DB21M` by:

- expanding the onboard memory from 32 GB to 64 GB;
- tweaking the chassis design (v1.0 -> v2.0) for reduced complexity and increased stiffness;
- introducing a newer version of the `HUT` (v3.15); which is backwards compatible and removes the need for an additional resistor on the top button;
- downgrades the IMU version from `MPU-9250` to `MPU-6050` due to global chip shortages (2021-2022 chip crisis).

To assemble a `DB21` Duckiebot, follow [these](#assembling-duckiebot-db21) instructions.

```{note}
You can obtain a `DB21` Duckiebot from the [Duckietown project shop](https://cutt.ly/Q81Lg4q).  
```

(duckiebot-config-db21m)= 
## Duckiebot MOOC Founder's edition, or `DB21M`

The `DB21M` is the first Duckiebot equipped with an NVIDIA Jetson Nano 2 GB computational unit instead of a Raspberry Pi.

The `DB21M` debuts in 2021 with the [first edition](https://cutt.ly/n81LRus) of the massive open online course, hosted on the edX platform.

```{figure} ../../_images/preliminaries_hardware/chap_2_1_images/db21m.jpg
:width: 400px
:name: fig:db21m

The Duckiebot version `DB21M`.
```
<!--
<div figure-id="fig:02-legacy" figure-caption="The Duckiebot version `DB21M`.">
   <img src="02-legacy.jpg" style='width: 20em'/>
</div>
-->

The `DB21M` is readily recognized by its blazing blue chassis and triple-decker configuration. It is equipped with a sensor suite including: camera, time-of-flight sensor, inertial measurement unit (IMU) and wheel encoders. Moreover, the `DB21M` features new electronics (HUT v3.1, front and back bumpers), a screen, a button and a custom designed [Duckiebattery](#db-opmanual-dtbattery-v2) (not to be confused with the [Duckie-power-bank](#db-opmanual-dtbattery-v1)).

To assemble a `DB21M` Duckiebot, follow [these](#assembling-duckiebot-db21m) instructions.
```{note}
`DB21M` Duckiebots are no longer manufactured. If you want to obtain one you might try to find inventory leftovers from Duckietown official distributors, or reach out to the [Duckietown hardware team](mailto:hardware@duckietown.com).  
```

<!--
[Duckietown project shop](https://get.duckietown.com/collections/dt-robots/products/duckiebot-db21-m).  
-->

(duckiebot-config-db19)=
## Duckiebot version 2019, or `DB19`

The `DB19` is the latest version of the Duckiebot. You have a `DB19` Duckiebot for sure if you have the blue motors shown in figure [](#fig:dc-motor-db19).

```{figure} ../../_images/preliminaries_hardware/chap_2_1_images/dc-motor-db19.png
:width: 400px
:name: fig:dc-motor-db19

The motors for the version `DB19`.
```
<!--
<div figure-id="fig:dc-motor-db19" figure-caption="The motors for the version `DB19`.">
   <img src="dc-motor-db19.png" style='width: 20em'/>
</div>
-->

Apart from the new motors and another HUT (v. 2.1), the `DB19` is identical with the `DB18`. A complete version can be seen here:

```{figure} ../../_images/preliminaries_hardware/chap_2_1_images/db19-complete-cad.png
:width: 400px
:name: fig:db19-complete-cad

The complete Duckiebot `DB19`.
```

<!--
<div figure-id="fig:db19-complete-cad" figure-caption="The complete Duckiebot 19">
   <img src="db19-complete-cad.png" style='width: 20em'/>
</div>
-->

To assemble a `DB19` Duckiebot, follow [these](#assembling-duckiebot-db19) instructions.

```{note}
`DB19` Duckiebots have been extremely successful but are no longer manufactured, and to the best of our knowledge only a few still exist unboxed. 
```
<!--
You can obtain a `DB19` Duckiebot from the [Duckietown project shop](https://get.duckietown.com/products/duckiebot-db19).  
-->

(duckiebot-config-db18)=
## Duckiebot version 2018, or `DB18` 

You have a `DB18` Duckiebot if, e.g., you have pledged to the Kickstarter.

There are two configuration of the `DB18`.

(duckiebot-config-db18-insight)=
### The `DB18` configuration

The main configuration is labeled plainly as `DB18` and is designed to operate on any Duckietown. You have the `DB18` if, e.g., you are a student attending the 2019 graduate level classes in ETH or the University of Montreal, or you have pledged to Summer 2018 Kickstarter.

The `DB18` supports different power bank models depending on the geographical region, but all these solutions are functionally equivalent, although their form factor is different.

You can recognize a `DB18` from previous versions for having only one board in addition to the Raspberry Pi, a backplate, and the computational stack mounted in the bottom deck.

```{figure} ../../_images/preliminaries_hardware/chap_2_1_images/howto_assemble_finish_milestone.jpg
:width: 400px
:name: fig:db18-battery1

A `DB18` Duckiebot assembly.
```

```{figure} ../../_images/preliminaries_hardware/chap_2_1_images/howto_assemble_finish_milestone-2.jpg
:width: 400px
:name: fig:db18-battery2

Another `DB18` Duckiebot assembly, with different battery.
```

<!--
<div figure-id="fig:db18-battery1" figure-caption="A Duckiebot DB18 assembly.">
   <img src="howto_assemble_finish_milestone.jpg" style='width: 20em'/>
</div>

<div figure-id="fig:db18-battery2" figure-caption="Another Duckiebot DB18 assembly, with a different battery.">
   <img src="howto_assemble_finish_milestone-2.jpg" style='width: 20em'/>
</div>
-->

To assemble a `DB18` Duckiebot, follow [these](#assembling-duckiebot-db18) instructions.

```{note}
`DB18` Duckiebots are no longer manufactured. There are very few unopened `DB18` boxes in the world. For additional information, reach out to contact the [Duckietown hardware team](mailto:hardware@duckietown.com).
```

<!--
You can obtain a `DB18` Duckiebot from the [Duckietown project shop](https://get.duckietown.com/products/duckiebot-db18).  
-->

(duckiebot-config-db18-robotarium)=
### The `DB18-Robotarium` configuration

The `DB18-Robotarium` configuration adds to the `DB18` the hardware necessary to operate in Robotariums (a.k.a. Duckietown Autolabs): continuously operating Duckietowns. They are otherwise identical to the `DB18`.

The additional hardware consists of a top localization April Tag infrastructure and an "auto-charging" mod, which allows Duckiebots to dock to charging stations and estimate the residual battery charge.  

Autolabs are experimental Duckietown features, currently under development. You will find `DB18-Robotarium` models in university research labs.

If you are interested in obtaining `DB18-Robotarium` Duckiebots, or in building your Duckietown Autolab, contact the [Duckietown team](mailto:info@duckietown.com).

```{figure} ../../_images/preliminaries_hardware/chap_2_1_images/a-glimpse-in-the-robotariums.png
:width: 400px
:name: fig:db18-robotarium

A Duckiebot in `DB18-Robotarium` configuration.
```
<!--
<div figure-id="fig:db18-robotarium" figure-caption="A Duckiebot in DB18-Robotarium configuration.">
   <img src="a-glimpse-in-the-robotariums.png" style='width: 25em'/>
</div>
-->

(duckiebot-config-db17)=
## Duckiebot versions 2017, or `DB17`

In the  `DB17` version, we had several configurations.

The configurations are defined with a root: `DB17-`, indicating the "bare bones" Duckiebot used in the Fall 2017 synchronized course, and an appendix `y` which can be the union (in any order) of any or all of the elements of the optional hardware set $\mathbb{O} = \{$`w`, `j`, `d`, `p`, `l`, `c`$\}$.

A `DB17` Duckiebot can navigate autonomously in a Duckietown, but cannot communicate with other Duckiebots.

The elements of $\mathbb{O}$ are labels identifying optional hardware that aids in the development phase and enables the Duckiebot to talk to other Duckiebots. The labels stand for:

- `w`: 5 GHz **w**ireless adapter to facilitate streaming of images;

- `j`: wireless **j**oypad that facilitates manual remote control;

- `d`: USB **d**rive for additional storage space;

- `c`: a different **c**astor wheel to _replace_ the preexisting omni-directional wheel;

- `p`: **P**WM hat for convenient powering of the DC motor hat;

- `l`: includes **L**EDs, LED hat, bumpers and the necessary mechanical bits to set the bumpers in place. Note that the installation of the bumpers induces the _replacement_ of a few `DB17` components;

<!--
Note: During the Fall 2017 course, three Duckietown Engineering Co. branches (Zurich, Montreal, Chicago) are using these configuration naming conventions. Moreover, all institutions release hardware to their Engineers in training in two phases.


For information on acquiring the parts for these older configurations please see [`DB17-wjd`](https://docs.duckietown.org/DT17/opmanual_duckiebot/out/acquiring_parts_c0.html) or [`DB17-wjdlc`](https://docs.duckietown.org/DT17/opmanual_duckiebot/out/acquiring_parts_c1.html).
-->

It may be convenient at times to refer to hybrid configurations including any of the `DB17-jwcd` in conjunction with a _subset_ of the `DB17-l` components. In order to disambiguate, we define partial upgrades as:

- `DB17-l1`: _adds_ a PWM hat to `DB17`, in addition to a short USB angled power cable and a M-M power wire;
- `DB17-l2`: _adds_ a bumpers set to `DB17`, in addition to the mechanical bits to assemble it;
- `DB17-l3`: _adds_ a LED hat and 5 RGB LEDs to `DB17-l1l2`, in addition to the F-F wires to connect the LEDs to the LED board.

Note: introducing the PWM hat in `DB17-l1` induces a _replacement_ of the [spliced cable](#assembling-duckiebot-db17-cable-splitting) powering solution for the DC motor hat. Details can be found in [](#assembling-duckiebot-db17).


- **Functions**: `DB17-l` is the necessary configuration to enable communication between Duckiebots, hence fleet behaviors (e.g., negotiating the crossing of an intersection). Subset configurations are sometimes used in a standalone way for: (`DB17-l1`) avoid using a sliced power cable to power the DC motor hat in `DB17`, and (`DB17-l2`) for purely aesthetic reasons.