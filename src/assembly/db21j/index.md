(assembling-duckiebot-db21j)=
# Assembly - Duckiebot `DB21-Jx`

```{needget}
* Duckiebot `DB21` parts ([get a `DB21-Jx`](https://get.duckietown.com/products/duckiebot-db21). If you are unsure what version of Duckiebot you have, check the overview of existing [Duckiebot configurations](duckiebot-configurations).

* A micro SD card with the Duckiebot image on it. The procedure to flash the SD card is explained [here](setup-duckiebot-sd-card).

* 3-4 hours of assembly time.
---
* An assembled Duckiebot in configuration `DB21J`.
```

## Foreword

These instructions are your friend. Follow them carefully, especially if it's the first time you assemble a Duckiebot. Small variations might cause big effects (e.g., don't flip your cables!).

```{todo}
**Video tutorial**

<div figure-id="fig:howto-assemble-02-legacy-rev1-video">
    <dtvideo src="vimeo:528621827"/>
</div>
```

## Overview

A Duckiebox contains the following components:

```{figure} ../../_images/assembly/db21j/db21-allcomponents.jpg
```

The assembly process is divided in 6 parts. They must be completed in the following order:

- [Part 1: Preliminary Steps](howto-preliminary-db21)
- [Part 2: Drive Train](howto-base-plate-db21)
- [Part 3: Computation Unit](howto-computation-db21)
- [Part 4: Rear Assembly](howto-rear-assembly-db21)
- [Part 5: Front Assembly](howto-front-assembly-db21)
- [Part 6: Top Deck Assembly](howto-top-deck-assembly-db21)
- [Troubleshooting section](op-faq-db21)

The Troubleshooting section at the bottom of this page provides resolutions to common problems.

(howto-preliminary-db21)=
## Preliminary Steps

### Unboxing

Unbox all of your components and lay them out on a flat surface. Ensure that you have well lit, uncluttered space to work on.

```{note}
"The Duckiebox hides but does not steal". Your Duckiebot chassis might be under the white protection foam inside the box. To reach it, pull out the white foam from the box after removing everything. Mind that the upper part of the inside foam has several side pockets in addition to a main compartment where components are located.
```

Although not necessary, a small (M2.5) wrench might ease some passages.

```{note}
Both NVIDIA Jetson Nano 2 GB and 4 GB are supported, but the SD cards must be initialized differently, as described in [](setup-duckiebot-sd-card).
```

### Plastic cover

Peel the plastic cover from all the chassis parts, on both sides.

### Screws, Nuts and Stand-offs

Verify each connecting part before using them. This will prevent undesirable effects (e.g., nylon screws prevent electrical shorts; bigger screws might damage the chassis).

```{figure} ../../_images/assembly/db21j/db21-rev1-parts-indices.png
:name: fig:db21m-rev1-parts-indices
```

(howto-preliminary-db21-battery)=
### Charge Duckiebattery via the `HUT`

This preliminary step allows us to start charging the battery while confirming the functionality of the `HUT`.

- Connect the battery and the `HUT` board as shown and make sure a green LED on the `HUT` is lit.
- Wait 30 minutes and then push the button on the battery.
- Check that the state of charge LEDs on the battery start blinking.
- Leave this setup until the battery is charged. This may take up to 5 hours.

```{figure} ../../_images/assembly/db21j/db21-rev1-step_00.png
```

You can familiarize with how the Duckiebattery works by reading its [handling instructions](db-opmanual-dtbattery-v2).

(howto-base-plate-db21)=
## Base-plate

In the following steps (1 to 16) we will build the *base-plate* assembly of the Duckiebot.


```{figure} ../../_images/assembly/db21j/db21-rev1-overview-step_01-16.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_01.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_02.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_03.jpg
```

```{figure} ../../_images/assembly/db21j/db21-rev1-step_04.jpg
```


```{note}
Occasionally manufacturing tolerances (on the nut and the chassis) might prevent a flush fit. Trying a different nut or changing its orientation might solve the problem.
```

```{figure} ../../_images/assembly/db21j/db21-rev1-step_05.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_06.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_07.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_08.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_09.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_10.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_11.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_12.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_13.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_14.jpg
```


```{figure} ../../_images/assembly/db21j/db21-rev1-step_15.jpg
```

Remove the USB cable from the Duckiebattery, connected in the [battery related preliminary step](howto-preliminary-db21-battery).

```{figure} ../../_images/assembly/db21j/db21-rev1-step_16.jpg
```

Before proceeding, verify that no component is wiggling. The only things moving should be the cables and the sphere in the omni-wheel (and, yes, the motor axles). Proceed to gently tighten the screws of the offending parts, if necessary.

(howto-computation-db21)=
## Computation Unit

The following steps (17 to 25) guide through the assembly of the *Computation* unit:


```{figure} ../../_images/assembly/db21j/db21-rev1-overview-step_17-25.jpg
```

<!--
You can try to mount the wheels even without the distance disks. But make sure that the wheels do not touch the frame of the Duckiebot when turning.

<div figure-id="fig:02-legacy-step_22B">
     <img src="db21-step_22B.png" style='width: 40em' />
</div>
-->



```{figure} ../../_images/assembly/db21j/db21-rev1-step_17.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_18.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_19.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_20.png
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_21.png
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_22.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_23.png
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_24.png
```

Now connect it to the base-plate (i.e, the rest of the chassis assembled in steps 1 to 16). Verify the chassis components are locked correctly.



```{figure} ../../_images/assembly/db21j/db21-rev1-step_25.jpg
```

(howto-rear-assembly-db21)=
## Rear Assembly

The following steps (26 to 39) guide through the assembly of the rear part of the Duckiebot:



```{figure} ../../_images/assembly/db21j/db21-rev1-overview-step_26-39.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_26.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_27.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_28.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_29.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_30.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_31.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_32.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_33.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_34.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_35.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_36.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_37.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_38.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_39.jpg
```

(howto-front-assembly-db21)=
## Front Assembly

Steps 40 to 52 guide you through the assembly of the front bumper:



```{figure} ../../_images/assembly/db21j/db21-rev1-overview-step_40-52.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_40.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_41.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_42.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_43.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_44.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_45.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_46.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_47.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_48.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_49.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_50.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_51.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_52.jpg
```

(howto-top-deck-assembly-db21)=
## Top Deck Assembly

This last section (steps 53 to 63) guide through the assembly of the top deck:



```{figure} ../../_images/assembly/db21j/db21-rev1-overview-step_53-63.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_53.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_54.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_55.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_56.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_57.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_58.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_59.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_60.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_61.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_62.jpg
```


(howto-power-db21)=
## Power your Duckiebot

One of the USB ports on the HUT will remain free. You can use this port to charge the Duckiebot. To avoid putting additional stress on the connector, you can leave this cable plugged in and store it under the blue top lid.

```{figure} ../../_images/assembly/db21j/db21-rev1-how2charge.png
```

```{warning}
*Always* plug and unplug USB cables from the `HUT` with care!
```

Once your Duckiebot is fully charged, you can press the button of the battery on the side to power it up (do this ONLY if a flashed SD card has been inserted). It is important to make sure the battery is charged to prevent undesired shutdown during the first boot, which will compromise the initialization sequence and require the sd card to be re-flashed.

```{figure} ../../_images/assembly/db21j/db21-rev1-step_63.jpg
```

Congratulations, your Duckiebot `DB21M` is now completely assembled.

(howto-additional-parts-db21)=
## Additional Parts

These additional parts are not always necessary.

### Back Pattern

The back pattern enables the traffic management behavior used in challenges with vehicles (e.g., `LFV`, `LFIV`, etc.).



```{figure} ../../_images/assembly/db21j/db21-rev1-step_64.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_65.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_66.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_67.jpg
```



```{figure} ../../_images/assembly/db21j/db21-rev1-step_68.jpg
```

### April Tag

This top facing April Tag enables localization in [Duckietown Autolabs](+opmanual_autolab#book).



```{figure} ../../_images/assembly/db21j/db21-rev1-step_69.jpg
```

## Check the outcome

* Look at the [Overview of interlocking parts](fig:db21m-rev1-parts-indices) and make sure you have used each type at least once.

* Check all cable connectors and make sure they are plugged in completely. Do not use force on the Duckiebot, it is (almost) never useful, and it might lead to undesirable outcomes.

* Make sure you have flashed your SD card with the latest version of the Duckiebot image (configuration `DB21M` if using a Jetson Nano 2 GB, `DB21J` if using a Jetson Nano 4 GB).

     ```{note}
     Version 1.2.2 is the minimum requirement for enabling battery code updates. Make sure you have at least this version (>22 March 2021).
     ```

* Make sure the SD card is inserted in Jetson Nano in the dedicated SD card slot under the main board. Do not plug it in the adapter and in a USB port. If you have already inserted a flashed SD card, you are allowed to push the magic button on the battery.


(op-faq-db21)=
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

````{trouble}
I can't screw the omni-directional wheel right; the screws don't fit all the way in the standoffs.

---
Occasionally the standoffs are not fully threaded due to manufacturing inefficiencies. The solution is to orient, in case of need, the shorter threaded stand-off side towards above, on the side of the chassis. Alternatively, shorter screws (provided in the package) can be used. If everything else fails, a "dirty" but effective solution is to use two spare nuts to mitigate tolerances, as shown in the picture below:


     ```{figure} ../../_images/assembly/db21j/db21-omni-dirtysolution.jpg
     ```

````

```{trouble}
A piece broke while I was trying to assemble it!

---
Mistakes happen. Some damages will not influence the functionality of the robot, others will be fixable at home with some tools, others could be showstoppers. Please take a picture of the damage and email hardware@duckietown.com for assistance.

```

````{trouble}
The wheels wiggle and/or fall off the motors.

---
This is due to manufacturing tolerances. You may remove the distance disks used in the assembly between motors and wheels, but make sure the wheels are not touching the screws of the motor mounts. Alternatively, screws are provided to fix the wheels to the motor axles. Make sure not to tighten the screws too hard, or they will add resistance to the spinning of the wheels (you can find the sweet spot by turning the wheel by hand and feeling the resistance torque).

     ```{figure} ../../_images/assembly/db21j/db21-wheel-screws.jpg

     Screws will keep the wheels in place. Do not tighten too hard!
     ```

````

```{trouble}
My Duckiebot is driving backwards when pressing the key for straight forward.

---
Try swapping the motor cables on the HUT connectors. Double-check the motor cables are connected to their respective ports as indicated above.

```

````{trouble}
I don't understand what's going on with the connections!

---
This simplified block diagram of data and electrical connections of the `DB21M` might help:

     ```{figure} ../../_images/assembly/db21j/db21-rev1-schematics-block-diagram.png

     Block diagram of electrical and data connections for the `DB21J` and `DB21M`.
     ```

````

````{trouble}
I have a non-functional sticker with weird symbols left over. What to do with it?

---
Duckiebots are FCC and CE certified, which means they comply with (and surpass) material quality (e.g., RoHS 2.0) and electrical interference standards (FCC, CE). You should place the sticker somewhere on the Duckiebot. We suggest a position out of sight (of other Duckiebots) to prevent detection issues in more advanced applications. For example, under the wheels:

```{figure} ../../_images/assembly/db21j/db21-fcc-ce-sticker.jpg

Place the sticker somewhere a human can read it, but another Duckiebot cannot.
```

````

```{trouble}
I followed the instruction to the letter, but there is something off I can't quite put my finger on.

---
You forgot to put a duckie on top of your Duckiebot!
