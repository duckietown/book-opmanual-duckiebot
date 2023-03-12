(get-db-hw)= 
# Getting the Duckiebot hardware

```{needget}
* Knowledge of [Duckiebot hardware configurations](duckiebot-configurations)
---
* Parts to assemble a Duckiebot.
```


(get-hw-foreword)=
## Foreword

You can acquire Duckiebots in two ways:

* **Do it yourself** (`DB17`): the `DB17` Duckiebot configuration is made of components that you can source independently.

* **"One click" solution** (`DB18` and above): you can source complete hardware kits on [the Duckietown project online store](https://cutt.ly/u81K1MU). These kits are tested to work with Duckietown software, are guaranteed to work, and come with a 12 months warranty.

<!--

## Acquiring the parts for a `DB18` {#db-opmanual-get-db18 status=ready}

Note that This hardware can be acquired by contacting directly the [Duckietown project](https://www.duckietown.org/about/hardware).

The `DB18` configuration has the same functionalities of a fully equipped `DB17-l` Duckiebot.

The `DB18` production has been discontinued in 2020.

-->

(db-opmanual-get-db17)=
## Acquiring the parts for a `DB17` 

Here, we provide a link to all bits and pieces that are needed to build a `DB17-jwd` Duckiebot, along with the price tag.

In general, keep in mind that:

- The links might expire, or the prices might vary.
- Shipping times and fees vary, and are not included in the prices shown below.
- International deliveries are subject to additional custom clearances and import fees.
- Substitutions are OK for the mechanical components,
  and not OK for all the electronics, unless you are OK in writing
  some software. Limited technical support will be offered for hardware customizations.
- Buying the parts for more than one Duckiebot makes each one cheaper than buying only one.
- For some components, the links we provide contain more bits than actually needed.

<!--
<div class='requirements' markdown="1">

Requires: Cost: USD 174 + Shipping Fees (minimal configuration `DB17`)

Requires: Time: 15 days (average shipping to the USA for cheapest choice of components)

Results: A kit of parts ready to be assembled in a `DB17` or `DB17-wjd` configuration.

Next steps: After receiving these components, you are ready to do some [soldering](#assembling-duckiebot-db17-soldering) before [assembling](#assembling-duckiebot-db17-ttic) your `DB17` or `DB17-wjd` Duckiebot.

</div>
-->

(get-db17-hw)=
### `DB17` Bill of materials 

```{list-table} DB17 Bill of materials
:header-rows: 1
:name: tab:materials

* - Item
  - Cost (USD)
* - [Chassis](http://www.kr4.us/magician-chassis-rob-12866.html)
  - 20
* - [Camera with 160-FOV Fisheye Lens](https://tinyurl.com/ybwrcywc)
  - 39
* - [Camera Mount](https://tinyurl.com/ybyewdrt)
  - 4
* - [300mm Camera Cable](https://www.adafruit.com/product/1648)        
  - 2
* - [Raspberry Pi 3 - Model B+](http://tinyurl.com/y66e43ks)
  - 39
* - [Heat Sinks](https://tinyurl.com/yanradnp)                         
  - 3
* - [Power supply for Raspberry Pi](https://www.adafruit.com/product/1995)
  - 7.50
* - [16 GB Class 10 MicroSD Card](http://tinyurl.com/y2dlbnfs)
  - 10
* - [Mirco SD card reader](https://www.adafruit.com/product/939)
  - 6 
* - [DC Motor HAT](https://tinyurl.com/y7qurpcw)
  - 22.50
* - [2 Stacking Headers](https://www.adafruit.com/product/2223)
  - 2.50/piece
* - [Battery Pack](https://tinyurl.com/ya7otc76)                        
  - 25
* - [16 Nylon Standoffs (M2.5 12mm F 6mm M)](https://tinyurl.com/y9uy73b2)
  - 0.06/piece
* - [4 Nylon Hex Nuts (M2.5)](https://tinyurl.com/ydy4znem)
  - 0.02/piece
* - [4 Nylon Screws (M2.5x10)](https://tinyurl.com/ya2uo9so)
  - 0.05/piece
* - [2 Zip Ties (300x5mm)](https://tinyurl.com/yb8v3nns)
  - 9
* - [Wireless Adapter (5 GHz)](https://tinyurl.com/ycvu7ok3) (`DB17-w`)
  - 25
* - [Joypad](https://tinyurl.com/y9klooef) (`DB17-j`)
  - 10.50
* - [Tiny 32GB USB Flash Drive](http://tinyurl.com/y4smbqe8) (`DB17-d`)
  - 10
* - [PWM/Servo HAT](https://tinyurl.com/yd8bdl2r) (`DB17-l1`)   
  - 17.50
* - [Power Cable](https://tinyurl.com/yaptpssu) (`DB17-l1`) 
  - 7.80
* - [Male-Male Jumper Wire](https://www.adafruit.com/products/1957) (`DB17-l1`) 
  - 1.95
* - [8 M3x10 pan head screws](https://www.mcmaster.com/#92005a120/=19lvrzk) (`DB17-l2`)
  - 7
* - [8 M3 nuts](https://www.mcmaster.com/#90591a250/=19lvsom) (`DB17-l2`) 
  - 7
* - Bumpers set (`DB17-l2`)  
  - 7 (custom made)
* - Bumper bracers set (`DB17-l2`)  
  - 7 (custom made)
* - [LEDs](https://www.adafruit.com/product/848) (`DB17-l3`) 
  - 10
* - [LED HAT](https://tinyurl.com/ydh9wqp5) (`DB17-l3`) 
  - 9/piece (but 3 pieces minimum)
* - [20 Female-Female Jumper Wires (300mm)](https://www.adafruit.com/products/793) (`DB17-l3`) 
  - 8
* - [4 4 pin female header](http://www.digikey.com/product-detail/en/PPTC041LFBN-RC/S7002-ND/810144) (`DB17-l3`) 
  - 0.60/piece
* - [12 pin male header](http://www.digikey.com/product-detail/en/amphenol-fci/68000-412HLF/609-3266-ND/1878525) (`DB17-l3`) 
  - 0.48/piece
* - [2 16 pin male header](http://www.digikey.com/product-detail/en/0022284160/WM50014-16-ND/313801) (`DB17-l3`) 
  - 0.61/piece
* - [3 pin male header](http://www.digikey.com/product-detail/en/M20-9990345/952-2263-ND/3728227) (`DB17-l3`) 
  - 0.10/piece
* - [2 pin female shunt jumper](http://www.digikey.com/product-detail/en/382811-8/A26228-ND/293121) (`DB17-l3`) 
  - 2/piece
* - [40 pin female header](https://www.adafruit.com/products/2222) (`DB17-l3`) 
  - 1.50
* - [5 200 Ohm resistors](https://tinyurl.com/yaramn3g) (`DB17-l3`) 
  - 0.10/piece
* - [10 130 Ohm resistors](https://tinyurl.com/y9vz2b9v) (`DB17-l3`) 
  - 0.10/piece
* - [Soldering tools](http://tinyurl.com/yyusy73b) 
  - 20
* - Total for `DB17` configuration                         
  - 193
* - Total for `DB17-w` configuration                         
  - 218
* - Total for `DB17-j` configuration                         
  - 203
* - Total for `DB17-d` configuration                         
  - 203
* - **Total for** `DB17-wjd` **configuration**                         
  - 238
* - **Total for** `DB17-l` **configuration**                         
  - 367
```

<!--
* - [300mm Camera Cable](https://www.adafruit.com/product/1648)                         
  - 2
* - [Raspberry Pi 3 - Model B+](http://tinyurl.com/y66e43ks)                         
  - 39
* - [Heat Sinks](https://tinyurl.com/yanradnp)                         
  - 3
* - [Power supply for Raspberry Pi](https://www.adafruit.com/product/1995)                         
  - 7.50
* - [16 GB Class 10 MicroSD Card](http://tinyurl.com/y2dlbnfs)                         
  - 10
* - [Mirco SD card reader](https://www.adafruit.com/product/939)
  - 6 
* - [DC Motor HAT](https://tinyurl.com/y7qurpcw)                         
  - 22.50
* - [2 Stacking Headers](https://www.adafruit.com/product/2223)
  - 2.50/piece
* - [Battery Pack](https://tinyurl.com/ya7otc76)                        
  - 25
* - [16 Nylon Standoffs (M2.5 12mm F 6mm M)](https://tinyurl.com/y9uy73b2)                         
  - 0.06/piece
* - [4 Nylon Hex Nuts (M2.5)](https://tinyurl.com/ydy4znem)                      
  - 0.02/piece
* - [4 Nylon Screws (M2.5x10)](https://tinyurl.com/ya2uo9so)
  - 0.05/piece
* - [2 Zip Ties (300x5mm)](https://tinyurl.com/yb8v3nns)                         
  - 9
* - [Wireless Adapter (5 GHz)](https://tinyurl.com/ycvu7ok3) (`DB17-w`)
  - 25
* - [Joypad](https://tinyurl.com/y9klooef) (`DB17-j`)                         
  - 10.50
* - [Tiny 32GB USB Flash Drive](http://tinyurl.com/y4smbqe8) (`DB17-d`)                         
  - 10
* - [PWM/Servo HAT](https://tinyurl.com/yd8bdl2r) (`DB17-l1`)   
  - 17.50
* - [Power Cable](https://tinyurl.com/yaptpssu) (`DB17-l1`) 
  - 7.80
* - [Male-Male Jumper Wire](https://www.adafruit.com/products/1957) (`DB17-l1`) 
  - 1.95
* - [8 M3x10 pan head screws](https://www.mcmaster.com/#92005a120/=19lvrzk) (`DB17-l2`)
  - 7
* - [8 M3 nuts](https://www.mcmaster.com/#90591a250/=19lvsom) (`DB17-l2`) 
  - 7
* - Bumpers set (`DB17-l2`)  
  - 7 (custom made)
* - Bumper bracers set (`DB17-l2`)  
  - 7 (custom made)
* - [LEDs](https://www.adafruit.com/product/848) (`DB17-l3`) 
  - 10
* - [LED HAT](https://tinyurl.com/ydh9wqp5) (`DB17-l3`) 
  - 9/piece (but 3 pieces minimum)
* - [20 Female-Female Jumper Wires (300mm)](https://www.adafruit.com/products/793) (`DB17-l3`) 
  - 8
* - [4 4 pin female header](http://www.digikey.com/product-detail/en/PPTC041LFBN-RC/S7002-ND/810144) (`DB17-l3`) 
  - 0.60/piece
* - [12 pin male header](http://www.digikey.com/product-detail/en/amphenol-fci/68000-412HLF/609-3266-ND/1878525) (`DB17-l3`) 
  - 0.48/piece
* - [2 16 pin male header](http://www.digikey.com/product-detail/en/0022284160/WM50014-16-ND/313801) (`DB17-l3`) 
  - 0.61/piece
* - [3 pin male header](http://www.digikey.com/product-detail/en/M20-9990345/952-2263-ND/3728227) (`DB17-l3`) 
  - 0.10/piece
* - [2 pin female shunt jumper](http://www.digikey.com/product-detail/en/382811-8/A26228-ND/293121) (`DB17-l3`) 
  - 2/piece
* - [40 pin female header](https://www.adafruit.com/products/2222) (`DB17-l3`) 
  - 1.50
* - [5 200 Ohm resistors](https://tinyurl.com/yaramn3g) (`DB17-l3`) 
  - 0.10/piece
* - [10 130 Ohm resistors](https://tinyurl.com/y9vz2b9v) (`DB17-l3`) 
  - 0.10/piece
* - [Soldering tools](http://tinyurl.com/yyusy73b) 
  - 20
* - Total for `DB17` configuration                         
  - 193
* - Total for `DB17-w` configuration                         
  - 218
* - Total for `DB17-j` configuration                         
  - 203
* - Total for `DB17-d` configuration                         
  - 203
* - **Total for** `DB17-wjd` **configuration**                         
  - 238
* - **Total for** `DB17-l` **configuration**                         
  - 367
-->

(db17-chassis)=
## Chassis

We selected the Magician Chassis as the basic chassis for the robot ([](fig:magician_chassis)).

We chose it because it has a double-decker configuration, and so we can put the battery in the lower part.

The chassis pack includes 2 DC motors and wheels as well as the structural part, in addition to a screwdriver and several necessary mechanical bits (standoffs, screws and nuts).

```{figure} ./chap_2_1_images/magician_chassis.jpg
:width: 15em
:name: fig:magician_chassis"

The "Magician" chassis was very popular. It is used in `DB17` through `DB19` Duckiebot models.
```

<!-- <div figure-id="fig:magician_chassis" figure-caption="The Magician Chassis">
     <img src="magician_chassis.jpg" style='width: 15em'/>
</div>
-->

(db17-rpi3b)=
## Raspberry Pi 3 - Model B

Note: It is recommended to upgrade to Raspberry Pi 3 model B+. In this case the 5 GHz wireless adapter is no longer necessary.

The Raspberry Pi is the central computer of the Duckiebot. Duckiebots use Model B ({numref}`fig:rpi3b`), a small but powerful computer.

```{figure} ./chap_2_1_images/rpi3b.png
:width: 15em
:name: fig:rpi3b

The Raspberry Pi 3 Model B is a 1.2GHz, 64-bit quad-core ARMv8 CPU, 1GB RAM little computer.
```

<!-- <div figure-id="fig:rpi3b" figure-caption="The Raspberry Pi 3 Model B">
     <img src="rpi3b.png" style='width: 15em'/>
</div> --> 

(db17-power)=
### Power Supply

We want a hard-wired power source (5VDC, 2.4A, Micro USB) to supply the Raspberry Pi ([](fig:power_supply)) while not driving. This charger can double down as battery charger as well.

```{figure} ./chap_2_1_images/power_supply.png
:width: 15em
:name: fig:power_supply

The power supply.
```

<!-- <div figure-id="fig:power_supply" figure-caption="The Power Supply">
     <img src="power_supply.png" style='width: 15em'/>
</div> --> 

(db17-heat-sinks)=
### Heat Sinks

The Raspberry Pi will heat up significantly during use. It is recommended adding heat sinks, as in  [](fig:heat_sinks). Since we will be stacking HATs on top of the Raspberry Pi with 15 mm standoffs, the maximum height of the heat sinks should be well below 15 mm. The chip dimensions are 15x15mm and 10x10mm.

```{figure} ./chap_2_1_images/heat-sinks.jpg
:width: 15em
:name: fig:heat_sinks

The heat sinks.
```

<!-- <div figure-id="fig:heat_sinks" figure-caption="The Heat Sinks">
     <img src="heat-sinks.jpg" style='width: 15em'/>
</div> -->

(db17-sdcard)=
###  Class 10 MicroSD Card

The MicroSD card ([](fig:SDcard)) is the hard disk of the Raspberry Pi. 16 GB of capacity are sufficient for the system image.

```{figure} ./chap_2_1_images/SDcard.png
:width: 15em
:name: fig:SDcard

The MicroSD card.
```

<!-- <div figure-id="fig:SDcard" figure-caption="The MicroSD card">
     <img src="SDcard.png" style='width: 15em'/>
</div> -->

(db17-sdcardreader)=
###  Mirco SD card reader

A microSD card reader ([](fig:microsd-reader)) is useful to copy the system image to a Duckiebot from a computer to the Raspberry Pi microSD card, when the computer does not have a native SD card slot.

```{figure} ./chap_2_1_images/microsd-reader.png
:width: 15em
:name: fig:microsd-reader

The Mirco SD card reader.
```

<!-- <div figure-id="fig:microsd-reader" figure-caption="The Mirco SD card reader">
     <img src="microsd-reader.png" style='width: 15em'/>
</div> -->

(db17-camera)=
## Camera

The Camera is the main sensor of the Duckiebot. All versions equip a 5 Mega Pixels 1080p camera with wide field of view ($160^\circ$) fisheye lens ([](fig:camera)).

```{figure} ./chap_2_1_images/camera.png
:width: 15em
:name: fig:camera

The Raspberry Pi camera with fisheye lens.
```

<!-- <div figure-id="fig:camera" figure-caption="The Camera with Fisheye Lens">
     <img src="camera.png" style='width: 15em'/>
</div> -->

(db17-cameramount)=
### Camera Mount

The camera mount ([](fig:camera_mount)) serves to keep the camera looking forward at the right angle to the road (looking slightly down). The front cover is not essential.

```{figure} ./chap_2_1_images/camera-mount.jpg
:width: 15em
:name: fig:camera_mount

The camera mount.
```

<!-- <div figure-id="fig:camera_mount" figure-caption="The Camera Mount">
     <img src="camera-mount.jpg" style='width: 15em'/>
</div> -->

The assembled camera (without camera cable), is shown in ([](fig:mounted-camera)).

```{figure} ./chap_2_1_images/mounted-camera.jpg
:width: 15em
:name: fig:mounted-camera

The camera on its mount.
```

<!-- <div figure-id="fig:mounted-camera" figure-caption="The Camera on its mount">
     <img src="mounted-camera.jpg" style='width: 15em'/>
</div> -->

(db17-cameracable300)=
### 300mm Camera Cable

A longer (300 mm) camera cable [](fig:long_camera_cable) makes assembling the Duckiebot easier, allowing for more freedom in the relative positioning of camera and computational stack.

```{figure} ./chap_2_1_images/long_camera_cable.png
:width: 15em
:name: fig:long_camera_cable

A 300 mm camera cable for the Raspberry Pi.
```

<!-- <div figure-id="fig:long_camera_cable" figure-caption="A 300 mm camera cable for the Raspberry Pi">
     <img src="long_camera_cable.png" style='width: 15em'/>
</div> -->

(db17-dc-motor-hat)=
## DC Motor HAT

We use the DC Stepper motor HAT ([](fig:motor_hat)) to control the DC motors that drive the wheels. This item will require [soldering](#assembling-duckiebot-db17-soldering) to be functional. This HAT has dedicate PWM and H-bridge for driving the motors.

```{figure} ./chap_2_1_images/motor_hat.png
:width: 15em
:name: fig:motor_hat

The stepper motor HAT.
```

<!-- <div figure-id="fig:motor_hat" figure-caption="The Stepper Motor HAT">
     <img src="motor_hat.png" style='width: 15em'/>
</div> -->

(db17-stackingheaders)=
### Stacking Headers

We use a long 20x2 GPIO stacking header ([](fig:stacking_header)) to connect the Raspberry Pi with the DC Motor HAT. This item will require [soldering](#assembling-duckiebot-db17-soldering) to be functional.

```{figure} ./chap_2_1_images/stacking_header.png
:width: 15em
:name: fig:stacking_header

The stacking headers.
```


<!-- <div figure-id="fig:stacking_header" figure-caption="The Stacking Headers">
     <img src="stacking_header.png" style='width: 15em'/>
</div> -->

(db17-battery)=
## Battery

The battery ([](fig:battery)) provides power to the Duckiebot.

We choose this battery because it has a good combination of size (to fit in the lower deck of the Magician Chassis), high output amperage (2.4A and 2.1A at 5V DC) over two USB outputs, a good capacity (10400 mAh) at an affordable price. The battery linked in the table above comes with two USB to microUSB cables.

```{figure} ./chap_2_1_images/battery-and-cables.jpg
:width: 15em
:name: fig:battery

The battery.
```

<!-- <div figure-id="fig:battery" figure-caption="The Battery">
     <img src="battery-and-cables.jpg" style='width: 15em'/>
</div> -->

(db17-standoffs)=
## Standoffs, Nuts and Screws

We use non electrically conductive standoffs (M2.5 12mm F 6mm M), nuts (M2.5), and screws (M2.5x10mm) to hold the Raspberry Pi to the chassis and the HATs stacked on top of the Raspberry Pi.

The Duckiebot requires 8 standoffs, 4 nuts and 4 screws.

```{figure} ./chap_2_1_images/mech-bits.jpg
:width: 15em
:name: fig:stands_nuts_screws

Standoffs, Nuts and Screws.
```


<!-- <div figure-id="fig:stands_nuts_screws" figure-caption="Standoffs, Nuts and Screws">
     <img src="mech-bits.jpg" style='width: 15em'/>
</div> -->

(db17-zipties)=
## Zip Ties

Two 300x5mm zip ties are needed to keep the battery at the lower deck from moving around.

```{figure} ./chap_2_1_images/zipties.png
:width: 15em
:name: fig:zipties

The zip ties.
```


<!-- <div figure-id="fig:zipties" figure-caption="The zip ties">
     <img src="zipties.png" style='width: 15em'/>
</div> -->

(db17-config-w)=
## Configuration `DB17-w`

(db17-wifi)=
### Wireless Adapter (5 GHz)

The Edimax AC1200 EW-7822ULC 5 GHz wireless adapter ([](fig:edimax)) boosts the connectivity of the Duckiebot, especially useful in busy Duckietowns (e.g., classroom). This additional network allows easy streaming of images.  

```{figure} ./chap_2_1_images/edimax.png
:width: 15em
:name: fig:edimax

The Edimax AC1200 EW-7822ULC WiFi adapter.
```


<!-- <div figure-id="fig:edimax" figure-caption="The Edimax AC1200 EW-7822ULC wifi adapter">
     <img src="edimax.png" style='width: 15em'/>
</div> -->

This component is not necessary if upgrading to Raspberry Pi 3 Model B+.

(db17-config-j)=
## Configuration `DB17-j`

(db17-joypad)=
### Joypad

The joypad is used to manually remote control the Duckiebot. Any 2.4 GHz wireless controller (with a _tiny_ USB dongle) will do.

The model linked in the table ([](fig:joystick)) does not include batteries.

```{figure} ./chap_2_1_images/joystick.png
:width: 15em
:name: fig:joystick

A Wireless joypad.
```


<!-- <div figure-id="fig:joystick" figure-caption="A Wireless Joypad">
     <img src="joystick.png" style='width: 15em'/>
</div> -->

Requires: 2 AA 1.5V batteries ([](fig:batteries)) not included in the [bill of materials](#tab:materials).

```{figure} ./chap_2_1_images/batteries.jpg
:width: 15em
:name: fig:batteries

Batteries.
```


<!-- <div figure-id="fig:batteries" figure-caption="A Wireless Joypad">
     <img src="batteries.jpg" style='width: 15em'/>
</div> -->

(db17-config-d)=
## Configuration `DB17-d`

(db17-flashdrive32)=
###  Tiny 32 GB USB Flash Drive

In configuration `DB17-d`, the Duckiebot is equipped with an "external" hard drive ([](fig:USBdrive)). This add-on is very convenient to store logs during experiments and later port them to a workstation for analysis. It provides storage capacity and faster data transfer than the MicroSD card.

```{figure} ./chap_2_1_images/USBdrive.png
:width: 15em
:name: fig:USBdrive

The tiny 32 GB USB flash drive.
```


<!-- <div figure-id="fig:USBdrive" figure-caption="The Tiny 32GB USB Flash Drive">
     <img src="USBdrive.png" style='width: 15em'/>
</div> -->

(db17-config-l)=
## Configuration `DB17-l`

(db17-leds)=
## LEDs

This Duckiebot is equipped with 5 RGB LEDs ([](fig:led)). LEDs can be used to signal to other Duckiebots, or just make _fancy_ patterns.

The pack of LEDs linked in the table above holds 10 LEDs, enough for two Duckiebots.

```{figure} ./chap_2_1_images/led.png
:width: 15em
:name: fig:led

The `DB17` RGB LEDs.
```


<!-- <div figure-id="fig:led" figure-caption="The RGB LEDs">
     <img src="led.png" style='width: 15em'/>
</div> -->

(db17-led-hat)=
### LED HAT

The LED HAT ([](fig:led_hat)) provides an interface for our RGB LEDs and the computational stack. This board is a daughterboard for the Adafruit 16-Channel PWM/Servo HAT, and enables connection with additional gadgets such as [ADS1015 12 Bit 4 Channel ADC](https://www.adafruit.com/product/1083), [Monochrome 128x32 I2C OLED graphic display](https://www.adafruit.com/product/931), and [Adafruit 9-DOF IMU Breakout - L3GD20H+LSM303](https://www.adafruit.com/product/1714). This item will require [soldering](#assembling-duckiebot-db17-soldering).

This board is custom designed and can only be ordered in minimum runs of 3 pieces. The price scales down quickly with quantity, and lead times may be significant, so it is better to buy these boards in bulk.

```{figure} ./chap_2_1_images/led_hat.png
:width: 25em
:name: fig:led_hat

The LED HAT.
```


<!-- <div figure-id="fig:led_hat" figure-caption="The LED HAT">
     <img src="led_hat.png" style='width: 15em'/>
</div> -->

(db17-pwm-servo-hat)=
### PWM/Servo HAT

The PWM/Servo HAT ([](fig:servo_hat)) mates to the LED HAT and provides the signals to control the LEDs, without taking computational resources away from the Rasperry Pi itself. This item will require [soldering](0_5_soldering_boards_c1.md).

```{figure} ./chap_2_1_images/servo_hat.png
:width: 15em
:name: fig:servo_hat

The PWM-Servo HAT.
```


<!-- <div figure-id="fig:servo_hat" figure-caption="The PWM-Servo HAT">
     <img src="servo_hat.png" style='width: 15em'/>
</div> -->

(db17-power-cable)=
### Power Cable

To power the PWM/Servo HAT from the battery, we use a short (30cm) angled male USB-A to 5.5/2.1mm DC power jack cable ([](fig:power-cable-usb-to-jack)).

```{figure} ./chap_2_1_images/power-cable-usb-to-jack.png
:width: 15em
:name: fig:power-cable-usb-to-jack

The 30cm angled USB to 5.5/2.1mm power jack cable.
```


<!-- <div figure-id="fig:power-cable-usb-to-jack" figure-caption="The 30cm angled USB to 5.5/2.1mm power jack cable.">
     <img src="power-cable-usb-to-jack.png" style='width: 15em'/>
</div> -->

(db17-mm-jumpers)=
### Male-Male Jumper Wires

The Duckiebot needs one male-male jumper wire ([](fig:mm_wires)) to power the DC Stepper Motor HAT from the PWM/Servo HAT.

```{figure} ./chap_2_1_images/mm_wires.png
:width: 15em
:name: fig:mm_wires

Male-male jumper wires.
```


<!-- <div figure-id="fig:mm_wires" figure-caption="Premier Male-Male Jumper Wires">
     <img src="mm_wires.png" style='width: 15em'/>
</div> -->

(db17-ff-jumpers)=
### Female-Female Jumper Wires

20 Female-Female Jumper Wires ([](fig:ff_wires)) are necessary to connect 5 LEDs to the LED HAT.

```{figure} ./chap_2_1_images/ff_wires.png
:width: 15em
:name: fig:ff_wires

Female-female jumper wires.
```


<!-- <div figure-id="fig:ff_wires" figure-caption="Premier Female-Female Jumper Wires">
     <img src="ff_wires.png" style='width: 15em'/>
</div> -->

(db17-bumpers)=
## Bumpers

These bumpers are designed to keep the LEDs in place and are therefore used only in configuration `DB17-l`. They are custom designed parts, so they must be produced and cannot be bought. We used laser cutting facilities.

<!--
Our design files are available [here].


```{figure} ./chap_2_1_images/placeholder.png
:width: 15em
:name: fig:bumpers

The bumpers.
```
-->

<!-- div figure-id="fig:bumpers" figure-caption="The Bumpers">
     <img src="placeholder.png" style='width: 15em'/>
</div -->

(db17-headers-resistors-jumpers)=
## Headers, resistors and jumper

Upgrading `DB17` to `DB17-l` requires several electrical bits: 5 of 4 pin female header, 2 of 16 pin male headers, 1 of 12 pin male header, 1 of 3 pin male header, 1 of 2 pin female shunt jumper, 5 of 200 Ohm resistors and finally 10 of 130 Ohm resistors.

These items require [soldering](0_5_soldering_boards_c1.md).

<!--
```{figure} ./chap_2_1_images/duckiebattery-voltage-profile.png
:width: 15em
:name: fig:duckiebattery-voltage-profile

The Duckie Power Bank output voltage drops when plugging in and removing teh charger.
```


div figure-id="fig:headers" figure-caption="The Headers">
     <img src="placeholder.png" style='width: 15em'/>
</div-->
<!--
```{figure} ./chap_2_1_images/duckiebattery-voltage-profile.png
:width: 15em
:name: fig:duckiebattery-voltage-profile

The Duckie Power Bank output voltage drops when plugging in and removing teh charger.
```


div figure-id="fig:resistors" figure-caption="The Resistors">
     <img src="placeholder.png" style='width: 15em'/>
</div-->

(db17-c-description)=
## Caster (`DB17-c`)

The caster ([](fig:caster)) is an `DB17-c` component that substitutes the steel omni-directional wheel that comes in the Magician Chassis package. Although the caster is not essential, it provides smoother operations and overall enhanced Duckiebot performance.

```{figure} ./chap_2_1_images/caster.png
:width: 15em
:name: fig:caster

The caster wheel.
```


<!-- <div figure-id="fig:caster" figure-caption="The caster wheel">
     <img src="caster.png" style='width: 15em'/>
</div> -->

To assemble the caster at the right height we will need to purchase:

- 4 standoffs (M3 12mm F-F) ([](fig:caster-standoffs)),
- 8 screws (M3x8mm) ([](fig:caster-screws)), and
- 8 split lock washers ([](fig:caster-split-washer)).

```{figure} ./chap_2_1_images/caster-standoffs.png
:width: 15em
:name: fig:caster-standoffs

Standoffs for caster wheel.
```
```{figure} ./chap_2_1_images/caster-screws.png
:width: 15em
:name: fig:caster-screws

Screws for caster wheel.
```
```{figure} ./chap_2_1_images/caster-split-washer.png
:width: 15em
:name: fig:caster-split-washer

Split lock washers for caster wheel.
```

<!-- <div figure-id="fig:caster-bits">
    <figcaption>Mechanical bits to assemble the caster wheel.</figcaption>

    <div figure-id="subfig:caster-standoffs" figure-caption="Standoffs for caster wheel.">
        <img src="caster-standoffs.png" style='width: 25em'/>
    </div> 

    <div figure-id="subfig:caster-screws" figure-caption="Screws for caster wheel.">
        <img src="caster-screws.png" style='width: 25em'/>
    </div> 

  <div figure-id="subfig:caster-split-washer" figure-caption="Split lock washers for caster wheel.">
        <img src="caster-split-washer.png" style='width: 25em'/>
    </div> 
</div> -->

```{note}
The caster wheel use is to be considered experimental and has been dropped in official configurations starting from `DB18`.

```
