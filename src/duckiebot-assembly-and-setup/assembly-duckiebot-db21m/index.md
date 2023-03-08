(assembling-duckiebot-db21m)=
# Assembly - Duckiebot `DB21M`

<!--

<div figure-id="fig:Duckiebook-Banner" figure-caption="The Duckiebot MOOC Founder's Edition, powered by NVIDIA Jetson Nano.">
     <img src="Duckiebook_Banner.png" style='width: 40em' />
</div>

-->

```{needget}
* Duckiebot `DB21M` parts ([get a `DB21M`](https://get.duckietown.com/)). If you are unsure what version of Duckiebot you have, check this overview of all existing [Duckiebot configurations](duckiebot-configurations).

* A micro SD card with the Duckiebot image on it. The procedure to flash the SD card is explained [here](setup-duckiebot).

* 3 hours of assembly time.
---
* An assembled Duckiebot in configuration `DB21M`.
```

## Foreword

These instructions are your friend. Follow them carefully, especially if it's the first time you assemble a `DB21M`. Small variations might cause big effects (e.g., don't flip your cables!).

(db21m-assembly-video)=
## Video tutorial

<div figure-id="fig:howto-assemble-db21m-video" figure-caption="DB21M: What's in the box and assembly.">
    <dtvideo src="vimeo:528621827"/>
</div>


## Overview

A Duckiebox contains the following components:

```{figure} ../../_images/assembly/db21m/db21-parts-overview.jpg
:width: 80%
:name: fig:db21m-parts-overview

Overview of all parts in your Duckiebox
```

The assembly process is divided in 9 parts. They must be completed in the following order:

- [Part 1: Preliminary Steps](howto-preliminary-db21m)
- [Part 2: Drive Train](howto-drive-train-db21m)
- [Part 3: Battery Pack Installation](howto-battery-pack-installation-db21m)
- [Part 4: Computational Unit and Rear Assembly](howto-comp-unit-db21m)
- [Part 5: Cable Management](howto-cables-db21m)
- [Part 6: Front Assembly](howto-front-assembly-db21m)
- [Part 7: Top Plate Assembly](howto-interactive-cover-db21m)
- [Part 8: Power your Duckiebot](howto-power-db21m)
- [Part 9: Additional Parts](howto-additional-parts-db21m)

- [Troubleshooting](op-faq-db21m)

The Troubleshooting section at the bottom of this page provides resolutions to common symptoms.

(howto-preliminary-db21m)=
## Preliminary Steps

### Unboxing

Unbox all of your components and lay them out on a flat surface. Ensure that you have well lit, uncluttered space to work on.

```{tip}
"The Duckiebox hides but does not steal". Your Duckiebot chassis is under the white protection foam. To get to the chassis, pull out the white foam from the box after removing everything. Mind that the upper part of the inside foam has several side pockets in addition to a main compartment where components are located.
```

Although not necessary, a small (M2.5) wrench might ease some of the next passages.

### Plastic cover

Peel the plastic cover from all the chassis parts on both sides.

### Screws, Nuts and Stand-offs

Each type of screw, nut and stand-off is labeled with an index. You will find corresponding labels on the pictures at each step. Using the right parts at each step will prevent undesirable effects (e.g., nylon screws prevent electrical shorts).

```{figure} ../../_images/assembly/db21m/db21-parts_indices.png
:width: 80%
:name: fig:db21m-parts_indices

Overview of interlocking parts
```


(howto-drive-train-db21m)=
## Drive Train

### Step 0 - Charge battery via `HUT`
- Connect the battery and the HUT board as shown and make sure a green LED on the HUT is lit.
- Wait 30 minutes and then push the button on the battery.
- Check that the state of charge LEDs on the battery start blinking.
- Leave this setup until the battery is fully charged. This may take up to 5 hours.


```{figure} ../../_images/assembly/db21m/db21-step_00.png
:width: 80%
:name: fig:db21-step_00
```
In the following steps (1 to 12) you will build the base plate assembly.

```{figure} ../../_images/assembly/db21m/db21-overview-step_01-12.png
:width: 80%
:name: fig:db21-overview-step_01-12
```



### Step 1
Take the baseplate (number `02` on the bottom side) and insert two metal M3 nuts (`N3`) as shown.

It might appear tricky at first to make the nuts fit. Once on the inset, gently rotate each nut until it falls in place (note the final orientation of the screw in the picture).

```{figure} ../../_images/assembly/db21m/db21-step_01.png
:width: 80%
:name: fig:db21-step-01
```

```{note}
Occasionally manufacturing tolerances (on the nut and the laser cut chassis) might prevent a flush fit. Trying a different nut or changing the insert direction might solve the problem.
```

### Step 2
Check the hole pattern in the middle of the plate to make sure you are holding it the right orientation, then insert two of the motor plates in the base plate.

```{figure} ../../_images/assembly/db21m/db21-step_02.png
:width: 80%
:name: fig:db21-step-02
```

### Step 3
Connect one of the 6-pin motor cable to the blue motor.

```{figure} ../../_images/assembly/db21m/db21-step_03.png
:width: 80%
:name: fig:db21-step_03
```

```{tip}
It might be easier if you place the base plate on a flat surface so hold the motor plates. Use one hand to hold the nut, and the other to drive the screwdriver.
```

### Step 4
Place the motor between the two plates and tighten it with two M3x30 screws (`B5`) and two metal M3 nuts (`N3`). Tighten the screws enough so that the final assembly does not wobble. Don't use excessive force to avoid getting hurt (or braking something).


```{figure} ../../_images/assembly/db21m/db21-step_04.png
:width: 80%
:name: fig:db21-step_04
```


```{warning}
Pre-bend the cable before carefully passing it through the cable management inset on the chassis. Don't use force to avoid braking the inset.
```
### Step 5
Connect the second 6-pin motor cable to the second motor.

```{figure} ../../_images/assembly/db21m/db21-step_05.png
:width: 80%
:name: fig:db21-step_05
```


### Step 6
Insert the other two motor plates into the base plate, similarly to step 2.

```{figure} ../../_images/assembly/db21m/db21-step_06.png
:width: 80%
:name: fig:db21-step_06
```

### Step 7
Tighten the second motor with two M3x30 metal screws (`B5`) and two metal M3 nuts (`N3`) and place the cable, similarly to steps 3 and 4.

```{figure} ../../_images/assembly/db21m/db21-step_07.png
:width: 80%
:name: fig:db21-step_07
```

### Step 8
Connect one of the longest 4-pin cables to the white connector of the IMU (Inertial Measurement Unit) board.

```{figure} ../../_images/assembly/db21m/db21-step_08.png
:width: 80%
:name: fig:db21-step_08
```

### Step 9
Attach the IMU board to the base plate using two nylon M2.5x10 screws (`B2`) and two nylon M2.5 nuts (`N2`).

```{figure} ../../_images/assembly/db21m/db21-step_09.png
:width: 80%
:name: fig:db21-step_09
```


### Step 10
Flip the assembly and verify that the three cables are routed through their corresponding holes or slits (cable of the *left* motor through the *left* slit, cable of the *right* motor through the *right* slit).

```{figure} ../../_images/assembly/db21m/db21-step_10.png
:width: 80%
:name: fig:db21-step_10
```

### Step 11
Flip the assembly again and mount the two M3x25 stand-offs (`S3`) to the bottom plate. Use two metal M3x8 screws (`B3`).

```{figure} ../../_images/assembly/db21m/db21-step_11.png
:width: 80%
:name: fig:db21-step_11
```


### Step 12
Mount the omni-wheel to the stand-offs using two of the metal M3x8 screws (`B3`).

```{figure} ../../_images/assembly/db21m/db21-step_12.png
:width: 80%
:name: fig:db21-step_12
```


```{tip}
If you note the screws don't go all the way, try flipping the stand-off.
```

### Verify the assembly

Before proceeding, verify that no component is wiggling. The only things moving should be the cables and the sphere in the omni-wheel (and, yes, the motor axles). Proceed to gently tightening the screws of the offending parts, if necessary.

Congratulations, you just built the base plate Duckiebot assembly!

(howto-battery-pack-installation-db21m)=
## Battery Pack Installation
The following steps (13 to 18) guide through the *Duckiebattery* assembly:

```{figure} ../../_images/assembly/db21m/db21-overview-step_13-18.png
:width: 80%
:name: fig:db21-step_13-18
```


<!--
You can try to mount the wheels even without the distance disks. But make sure that the wheels do not touch the frame of the Duckiebot when turning.

<div figure-id="fig:db21-step_22B">
     <img src="db21-step_22B.png" style='width: 40em' />
</div>

-->

### Step 13
Take the upper plate (`01`) and 8 metal M3 nuts (`N3`). Compare the hole in the green circles with the hole position on your plate and make sure they agree (if the number `01` is visible on top, you are good to go).

```{figure} ../../_images/assembly/db21m/db21-step_13.png
:width: 80%
:name: fig:db21-step_13
```

### Step 14
Insert 4 nylon M2.5x10 screws (`B2`) from the top and tighten them with 4 nylon M2.5 nuts (`N2`).

```{figure} ../../_images/assembly/db21m/db21-step_14.png
:width: 80%
:name: fig:db21-step_14
```


### Step 15
Take the two plates with numbers `04L` and `04R` and insert three metal M3 nuts (`N3`) into each of them.

```{figure} ../../_images/assembly/db21m/db21-step_15.png
:width: 80%
:name: fig:db21-step_15
```


### Step 16
Connect these two plates to the upper plate with a metal M3x8 screw (`B3`) each. Note the slightly different holes in the side plates to mount them in the right way!

```{figure} ../../_images/assembly/db21m/db21-step_16.png
:width: 80%
:name: fig:db21-step_16
```


### Step 17
Insert the battery between the two side plates. Make sure the Mack the duck is on the bottom. The USB ports of the battery are not the same. Flipping the battery at this stage will cause the Duckiebot not to power on.

```{figure} ../../_images/assembly/db21m/db21-step_17.png
:width: 80%
:name: fig:db21-step_17
```


```{figure} ../../_images/assembly/db21m/db21-step_17additional.png
:width: 80%
:name: fig:db21-step_17additional
```


### Step 18
Take the two small plates labeled `07` and lock the battery in place.

```{figure} ../../_images/assembly/db21m/db21-step_18.png
:width: 80%
:name: fig:db21-step_18
```


(howto-comp-unit-db21m)=
## Computation Unit and Rear Assembly
At this point, we are starting to see the final shape of the Duckiebot! The following steps (19 to 27) will help assemble the lower frame and mount the NVIDIA Jetson Nano board:

```{figure} ../../_images/assembly/db21m/db21-overview-step_19-27.png
:width: 80%
:name: fig:db21-overview-step_19-27
```


### Step 19
Take the lower half of the Duckiebot from steps 1 to 12 again and mount it directly to the assembly you have just created using 4 metal M3x8 (`B3`) screws. Make sure all the plates are locked in place correctly.

```{figure} ../../_images/assembly/db21m/db21-step_19.png
:width: 80%
:name: fig:db21-step_19
```


```{attention}
This is a tricky step and might require a few tries to get it right. Remember that the Roboticist is patient and welcomes challenges with joy and determination!
```

### Step 20
Check the routing path of the two motor cables again from step 10 and wire them through the holes in the upper plate.

```{figure} ../../_images/assembly/db21m/db21-step_20.png
:width: 80%
:name: fig:db21-step_20
```


### Step 21
Do a similar procedure for the cable of the IMU unit.

```{figure} ../../_images/assembly/db21m/db21-step_21.png
:width: 80%
:name: fig:db21-step_21
```


### Step 22
Take the two yellow driving wheels and push them to the motors using one distance disk (`S4`) between each of them.

```{figure} ../../_images/assembly/db21m/db21-step_22.png
:width: 80%
:name: fig:db21-step_22
```


### Step 23
1. Insert the SD card to the slot on the NVIDIA Jetson Nano board. Make sure the metal pins of the SD card are facing the heat sink.

2. Place the Jetson Nano on the 4 screws from step 14 but DO NOT tighten the Jetson with any nuts or stand-offs yet!

```{figure} ../../_images/assembly/db21m/db21-step_23.png
:width: 80%
:name: fig:db21-step_23
```



### Step 24
Take the side cover carrying the number `05L`. Insert a nylon M2.5 nut (`N2`) and a metal M3 nut (`N3`) into the plate (note the engravings: `N2` and `N3` on the plate itself).

Then secure the plate to the frame using two metal M3x8 screws (`B3`).

You may need to lift the Jetson Nano a little to fit the side cover plate under the NVIDIA Jetson Nano board.

```{figure} ../../_images/assembly/db21m/db21-step_24.png
:width: 80%
:name: fig:db21-step_24
```


### Step 25
Place 4 of the (`S5`) spacers on the nylon screws holding the NVIDIA Jetson Nano board.

```{figure} ../../_images/assembly/db21m/db21-step_25.png
:width: 80%
:name: fig:db21-step_25
```


### Step 26
Tighten the NVIDIA Jetson Nano board with the 6 brass stand-offs (`S2`). Put two stand-offs on each of the front screws but only one each on the back.

```{figure} ../../_images/assembly/db21m/db21-step_26.png
:width: 80%
:name: fig:db21-step_26
```

### Step 27
Take the side cover carrying the number `05R`. Insert a nylon M2.5 nut (`N2`) and a metal M3 nut (`N3`) into the plate, similarly to step 24 (note the engraving: `N2` and `N3` on the plate itself). Then screw the plate to the frame using two metal M3x8 screws (`B3`).

```{figure} ../../_images/assembly/db21m/db21-step_27.png
:width: 80%
:name: fig:db21-step_27
```


(howto-cables-db21m)=
## Cable Management

### Step 28
Take the USB cable that has three connectors. Connect the Duckiebattery and the NVIDIA Jetson Nano board with the USB-A ports as shown in the picture below.

```{figure} ../../_images/assembly/db21m/db21-step_28.png
:width: 80%
:name: fig:db21-step_28
```


```{attention}
The micro USB connector must **not** be connected at that stage!
```

### Step 29

Take the angled micro USB to micro USB cable and plug the angled connector to the middle port on the Duckiebattery. Wire the cable through the chassis as shown in the picture below. The micro USB end must be unplugged at that stage!

```{tip}
An experienced Roboticist at this point would mark the free end of this cable (e.g., with a sticker or some tape), to make it distinguishable from the other free roaming cable with a micro USB connector, so to make it very improbable to mix the two up and prevent future headaches!
```

```{figure} ../../_images/assembly/db21m/db21-step_29.png
:width: 80%
:name: fig:db21-step_29
```


### Step 30
Now take the last USB cable, with a micro USB plug on one side and an angled USB-A plug on the other side. Connect the USB-A end to the last (right) port on the Duckiebattery. Again, wire the cable through the chassis as shown and leave the micro USB connector free on the other side.

```{figure} ../../_images/assembly/db21m/db21-step_30.png
:width: 80%
:name: fig:db21-step_30
```


### Step 31
Connect the Wi-Fi dongle to the upper USB-A port on the NVIDIA Jetson Nano board.

```{figure} ../../_images/assembly/db21m/db21-step_31.png
:width: 80%
:name: fig:db21-step_31
```


### Step 32
Take the back bumper board and connect the 4-pin cable of medium length to the white plug on the board.

```{figure} ../../_images/assembly/db21m/db21-step_32.png
:width: 80%
:name: fig:db21-step_32
```


### Step 33
Wire the cable attached to the back bumper through the same hole in the upper plate as the motor cable of the left driving motor.

```{figure} ../../_images/assembly/db21m/db21-step_33.png
:width: 80%
:name: fig:db21-step_33
```


### Step 34
When attaching the back bumper board to the chassis, make sure the pins of the lower and upper plate all fit well. Tighten the board with three metal screws (`B3`).

```{figure} ../../_images/assembly/db21m/db21-step_34.png
:width: 80%
:name: fig:db21-step_34
```


### Step 35
Take the plate carrying the number `06` and press two nylon M2.5 nuts (`N2`) into the corresponding slits.

```{figure} ../../_images/assembly/db21m/db21-step_35.png
:width: 80%
:name: fig:db21-step_35
```


### Step 36
Mount the plate number `06` to the back of the chassis using two metal M3x8 screws (`B3`).

```{attention}
The `06` is not symmetric and the orientation matters. If the number `06` is pointing towards the Duckiebot, we are good to go!
```

```{figure} ../../_images/assembly/db21m/db21-step_36.png
:width: 80%
:name: fig:db21-step_36
```


### Step 37
Take the fan and mount it on top of the heat sink of the NVIDIA Jetson Nano board using 4 metal M3x12 screws (`B4`). Make sure the cable of the fan is pointing to the back right side (it might be necessary to use a little force on these screws, as the thread has to cut it's way through the heat sink the first time).

```{note}
You don't need to tighten the screws completely but the fan must sit tight.
```

```{figure} ../../_images/assembly/db21m/db21-step_37.png
:width: 80%
:name: fig:db21-step_37
```


### Step 38

Take the PCB with the Duckietown logo on it (we'll call it the `HUT` from now on. A `DB21M` is equipped with a `HUT` v3.1). 

```{figure} ../../_images/assembly/db21m/hutv31-layout.png
:width: 80%
:name: fig:HUT_layout
```

Plug in the fan cable to the two pins as shown (note the orientation of the black and red cables!).

```{figure} ../../_images/assembly/db21m/db21-step_38.png
:width: 80%
:name: fig:db21-step_38
```


### Step 39
Gently press the pin connector of the `HUT` on the pins on the NVIDIA Jetson Nano board. Make sure both motor cables are routed through the slit in the `HUT` board.

```{figure} ../../_images/assembly/db21m/db21-step_39.png
:width: 80%
:name: fig:db21-step_39
```

### Step 40
Connect the `HUT` to the plate in the back using two nylon M2.5x10 screws (`B2`). Make sure the end of the 4-pin cable connected to the back bumper board is pointing to the right hand side.

```{figure} ../../_images/assembly/db21m/db21-step_40.png
:width: 80%
:name: fig:db21-step_40
```

### Step 41
Connect the 4-pin cable of the back bumper board to the white connector in the back right corner of the `HUT`.

```{figure} ../../_images/assembly/db21m/db21-step_41.png
:width: 80%
:name: fig:db21-step_41
```


### Step 42
Connect the first 6-pin motor cable of the left motor to the connector placed on the edge of the `HUT`.

```{figure} ../../_images/assembly/db21m/db21-step_42.png
:width: 80%
:name: fig:db21-step_42
```

### Step 43
Connect the second 6-pin motor cable of the right motor to the other connector.

```{figure} ../../_images/assembly/db21m/db21-step_43.png
:width: 80%
:name: fig:db21-step_43
```

```{note}
If you swap the motor cables, you Duckiebot will probably drive backwards when it is supposed to drive forwards :)
```

### Step 44
Connect the 4-pin cable from the IMU to the corresponding plug shown in the picture.

```{figure} ../../_images/assembly/db21m/db21-step_44.png
:width: 80%
:name: fig:db21-step_44
```


(howto-front-assembly-db21m)=
## Front Assembly
The following steps 45 to 52 will guide you through the assembly of the camera unit as well as some more electronics and cables.

```{figure} ../../_images/assembly/db21m/db21-overview-step_45-52.png
:width: 80%
:name: fig:db21-overview-step_45-52
```

### Step 45
If not already done, open the plug of the camera and push one side of the camera cable in. The orientation of the cable should be such that the copper pins on the camera cable face the camera plate. Then close the plug completely. Make sure to take off the plastic cap from the lens.

```{figure} ../../_images/assembly/db21m/db21-step_45.png
:width: 80%
:name: fig:db21-step_45
```

### Step 46
Wire the camera cable through the 3D printed camera mount starting from the front. Then use 4 nylon M2x8 screws (`B1`) and 4 nylon M2 nuts (`N1`) on the other side to tighten the camera to the mount.

```{figure} ../../_images/assembly/db21m/db21-step_46.png
:width: 80%
:name: fig:db21-step_46
```

### Step 47
Mount the camera part to the front bumper board using only one metal M3x8 screw (`B3`) and one metal M3 nut (`N3`).

```{figure} ../../_images/assembly/db21m/db21-step_47.png
:width: 80%
:name: fig:db21-step_47
```


### Step 48
Mount the single nylon M3x5 stand-off (`S1`) with a metal M3x8 screw (`B3`) from the other side.

```{figure} ../../_images/assembly/db21m/db21-step_48.png
:width: 80%
:name: fig:db21-step_48
```


### Step 49
Take one of the longest 4-pin cables and connect it to the front bumper board as shown.

```{figure} ../../_images/assembly/db21m/db21-step_49.png
:width: 80%
:name: fig:db21-step_49
```

### Step 50
Wire the cable that you have just connected (step 49) through the upper plate and the connect it to the connector on the `HUT`, as shown below.

```{figure} ../../_images/assembly/db21m/db21-step_50.png
:width: 80%
:name: fig:db21-step_50
```


### Step 51
Take the last of the long 4-pin cables and connect it to the front bumper board, similarly to step 49.

```{figure} ../../_images/assembly/db21m/db21-step_51.png
:width: 80%
:name: fig:db21-step_51
```

### Step 52
Again, wire this cable through the upper plate and connect it to the `HUT`, similarly to step 50.

```{figure} ../../_images/assembly/db21m/db21-step_52.png
:width: 80%
:name: fig:db21-step_52
```


### Step 53
Mount the front bumper board to the upper and lower plate using three metal M3x8 screws (`B3`). Make sure they are locked in place correctly.

```{figure} ../../_images/assembly/db21m/db21-step_53.png
:width: 80%
:name: fig:db21-step_53
```


### Step 54
Open the camera slit on the NVIDIA Jetson Nano board by raising it on the sides (with care), and put in the other end of the camera cable.

```{attention}
The orientation of the cable should be such that the blue part of the cable faces the camera (i.e., facing towards the front end of the Duckiebot).
```

```{figure} ../../_images/assembly/db21m/db21-step_54.png
:width: 80%
:name: fig:db21-step_54
```


### Step 55
Attach the small blue distance sensor to the stand-off on the front bumper and tighten it with a nylon M3 nut (`N4`).

```{figure} ../../_images/assembly/db21m/db21-step_55.png
:width: 80%
:name: fig:db21-step_55
```


Make sure to take off the small transparent cover from the sensor.

```{figure} ../../_images/assembly/db21m/db21-step_55A.png
:width: 80%
:name: fig:db21-step_55A
```


### Step 56
Take the shortest 4-pin cable and connect the bottom of the time of flight sensor to the front bumper, as shown below.

```{figure} ../../_images/assembly/db21m/db21-step_56.png
:width: 80%
:name: fig:db21-step_56
```


(howto-interactive-cover-db21m)=
## Top Plate Assembly
The following steps 57 to 64 show the assembly of the top plate of the `DB21M`, containing a button and a screen.

```{figure} ../../_images/assembly/db21m/db21-overview-step_57-59.png
:width: 80%
:name: fig:db21-overview-step_57-59
```


### Step 57
Remove the nut from the button, if necessary, and wire the button cables through the hole on the top plate  (marked as `03`).

```{attention}
Mind the orientation; if the number is pointing downwards, we are good to go!
```

Once the button is pushed in completely, tighten it again with the flat nut.

```{figure} ../../_images/assembly/db21m/db21-step_57.png
:width: 80%
:name: fig:db21-step_57
```

### Step 58
Mount the screen to the plate in a way the pins of the screen are pointing towards the button. Use 4 nylon M2.5 screws (`B2`) and 4 nylon M2.5 nuts (`N2`) for this.

```{figure} ../../_images/assembly/db21m/db21-step_58.png
:width: 80%
:name: fig:db21-step_58
```

### Step 59
Have a look at the pin descriptions on the screen. Take the 4-pin cable with the long black connectors and connect the 4 loose ends to the screen.

Follow this pattern: GND-black, VCC-red, SCK-yellow, SDA-blue.

```{figure} ../../_images/assembly/db21m/db21-step_59.png
:width: 80%
:name: fig:db21-step_59
```

### Step 60
Connect the end of the cable from the button to the connector on the `HUT`, as below.

```{figure} ../../_images/assembly/db21m/db21-step_60.png
:width: 80%
:name: fig:db21-step_60
```


### Step 61
Connect the end of the cable from the screen to the 4 male pins on the `HUT` as shown. Check the colors of the cables so that the same goes to the same, i.e.: GND-black, 3.3V-red, SCL-yellow, SDA-blue.

```{figure} ../../_images/assembly/db21m/db21-step_61.png
:width: 80%
:name: fig:db21-step_61
```


### Step 62
Gently place the cover plate on the chassis. Make sure the screws of the fan and the pins of the side plates are locked in place properly.

```{figure} ../../_images/assembly/db21m/db21-step_62.png
:width: 80%
:name: fig:db21-step_62
```


### Step 63
Tighten the cover part using two nylon M2.5x10 screws (`B2`).

```{figure} ../../_images/assembly/db21m/db21-step_63.png
:width: 80%
:name: fig:db21-step_63
```

### Step 64
Then, tighten the cover using two nylon M2.5 nuts (`N2`).

```{figure} ../../_images/assembly/db21m/db21-step_64.png
:width: 80%
:name: fig:db21-step_64
```


(howto-power-db21m)=
## Power your Duckiebot

In this step we will plug the various power cables to the `HUT`. One port will remain free. You can use this port to charge the Duckiebot.

```{figure} ../../_images/assembly/db21m/db21-how2charge.png
:width: 80%
:name: fig:db21-how2charge
```

```{warning}
*Always* plug and unplug USB cables from the `HUT` with care!
```

### Step 65
Take the black USB cable that you have connected in step 29 and connect it to the micro USB connector on the `HUT` as shown.

```{figure} ../../_images/assembly/db21m/db21-step_65.png
:width: 80%
:name: fig:db21-step_65
```

### Step 66
Similarly, connect the other USB cable (routed through the same hole) to the `HUT`.

```{figure} ../../_images/assembly/db21m/db21-step_66.png
:width: 80%
:name: fig:db21-step_66
```

### Step 67
Finally, connect the last cable to the `HUT`.

```{figure} ../../_images/assembly/db21m/db21-step_67.png
:width: 80%
:name: fig:db21-step_67
```

### Step 68
At that point, your Duckiebot is fully assembled!
For charging, connect the charging cable to the last free micro USB connector on the `HUT`. To avoid putting additional stress on the connector, you can leave this cable plugged in and store it somewhere under the blue top lid.

```{figure} ../../_images/assembly/db21m/db21-step_68A.png
:width: 80%
:name: fig:db21-step_68A
```

Once your Duckiebot is fully charged, you can press the button of the battery on the side to power it up (do this ONLY if a flashed SD card has been inserted).

```{figure} ../../_images/assembly/db21m/db21-step_68B.png
:width: 80%
:name: fig:db21-step_68B
```

(howto-additional-parts-db21m)=
## Additional Parts

### Step 69
If you have an April tag take some glue and put it in between the two nylon screws on the top of you Duckiebot.

```{figure} ../../_images/assembly/db21m/db21-step_69.png
:width: 80%
:name: fig:db21-step_69
```

### Step 70
If you have a circle pattern put it on the back plate of your Duckiebot.

```{figure} ../../_images/assembly/db21m/db21-step_70.png
:width: 80%
:name: fig:db21-step_70
```

## Check the outcome



* Look at the [](fig:db21m-parts_indices) and make sure you have used each type at least once.

* Check all cable connectors and make sure they are plugged in completely. Do not use force on the Duckiebot, it is (almost) never useful and it might lead to undesirable outcomes.

* Make sure all USB cables to the Jetson Nano and the `HUT` are plugged in completely, and in the correct order. Several configurations exist for which the Duckiebot will do _something_, but only one, described above, is the correct one.

* Make sure you have flashed your SD card with the latest version of the Duckiebot `DB21M` image.

     ```{note}
     Version 1.2.2 is the minimum requirement for enabling battery code updates. Make sure you have at least this version (>22 March 2021).
     ```

* Make sure the SD card is inserted in Jetson Nano in the dedicated SD card slot under the main board. Do not plug it in the adapter and in a USB port. If you have already inserted a flashed SD card, you are allowed to push the magic button on the battery.


(op-faq-db21m)=
## Troubleshooting

```{trouble}
I can't find the blue chassis.

---
It's *under* the white foam in the Duckiebox. Remove the inner packaging to access it.
```

```{trouble}
Camera cable needs to be twisted to make the pins on the cable matching those in the connector. Is this normal?

---
Yes this is normal. It might look a little nicer if you wire the camera cable around the metal stand-off next to the plug.

```

```{trouble}
The Duckiebattery does not fit flush in the compartment.

---
Position it as it fits (at an angle). It will make the assembly a little trickier but everything will work out in the end.

```

```{trouble}
I don't have enough screws of a specific type.

---
Each package has enough screws of each type, plus spares of some. It might happen to inadvertently use one type instead of the correct one, which will result in shortages towards the final stages. Following the instructions carefully will prevent this from happening.

```

```{trouble}
I can't screw the omni-directional wheel right; the screws don't fit all the way in the standoffs.

---
Sometimes manufacturing inefficiencies make the thread inside the standoff shorter than it should. This happens only occasionally and it is not the norm. The solution is to orient, in case of need, the shorter threaded stand-off side towards above, on the side of the chassis.

```

```{trouble}
A piece broke while I was trying to assemble it!

---
Mistakes happen. Some damages will not influence the functionality of the robot, others will be fixable at home with some tools, others could be showstoppers. Please take a picture of the damage and send an email to hardware@duckietown.com.

```

```{trouble}
The wheels tend to fall off the motors.

---
You may remove the distance disks you put in step 22. But make sure that the wheels are still not touching the screws of the motor mounts.

```

```{trouble}
My Duckiebot is driving backwards when pressing the key for straight forward.

---
You have swapped the motor cables. Please check the steps 42 and 43 again and make sure you connected the cables the right way.

```

````{trouble}
One of the black USB cables is too short to connect it to the HUT.

---
The customized cables may undergo some manufacturing tolerances. If it does not fit, there is a second way to connect the cables. However, some minor functionalities might differ in that configuration (e.g. the fan might continue working when shutting down the NVIDIA Jetson Nano). 

![](../../_images/assembly/db21m/db21-step_65-67.jpg)

````

````{trouble}
I don't understand what's going on with the connections

---
This simplified block diagram of data and electrical connections of the `DB21M` might help:

![](../../_images/assembly/db21m/db21-schematics-block-diagram.png)
<!--      ```{figure} ../../_images/assembly/db21m/db21-schematics-block-diagram.png
     :width: 80%
     :name: fig:db21m-block-diagram

     `DB21M` block diagram of electrical and data connections
     ``` -->

````

```{trouble}
I followed the instruction to the letter, but there is something off I can't quite put my finger on.

---
You forgot to put a duckie on top of your Duckiebot!
```
