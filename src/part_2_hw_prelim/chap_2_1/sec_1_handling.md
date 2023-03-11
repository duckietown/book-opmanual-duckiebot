(db-opmanual-preliminaries-electronics)= 
# Handling circuits and batteries

<div class='requirements' markdown="1">

Requires: Nothing

Results: Preliminary knowledge on circuits and power source properties useful in Duckietown

</div>

Duckiebots support several power bank models, although not all power sources will work. Here, we list properties of the supported models.

(db-opmanual-dtbattery-v2)=
## The Duckiebattery (`DB-C-DBatt`)

This battery is the standard battery for the Duckiebots since 2021. For example, models `DB21M`, `DB21`, `DB-J`, `DB-R` use this battery.

The Duckiebattery is special because it is a programmable, smart battery, designed and manufactured specifically for Duckiebots. Using this battery will allow your Duckiebot to monitor the state of charge and other diagnostics, and shutdown via software. Moreover, it enables advanced features such as auto-charging in Autolabs, because it will guarantee power to the onboard computer when being plugged in or out of charge. 

<!--
```{figure} ./chap_2_1_images/DB-C-DBatt_real2.jpg
:width:
:name:

Caption
```

[comment]: <> (<div figure-id="fig:DB-C-DBatt_real" figure-caption="The Duckiebattery.">)

[comment]: <> (     <img src="DB-C-DBatt_real2.jpg" style='width: 15em' />)

[comment]: <> (</div>)
-->



```{figure} ./chap_2_1_images/DB-C-DBatt_real2.jpg
:width: 200px
:name: fig:DB-C-DBatt_real

The Duckiebattery.
```

(db-opmanual-dtbattery-v2-tech-specs)=
### Technical specification

- Capacity: 10Ah at 3.7V
- Charging: Micro USB 5V at up to 2A
- Output 2 x USB type A 5V at up to 4A (combined), max 2.5A on a single port
- Charge time: 0-100% takes about 5h and 0-90% about 4h with a 2A power supply
- Weight: 189g (fully charged)

```{caution}
Lithium-ion batteries like the Duckiebattery are potentially dangerous and must be handled with care. 
```
Here are some things to do and not to do. 

```{warning}
Keep reading the following safety precautions: do not skip this section.
```
(db-opmanual-dtbattery-v2-dos)=
### Handling: things to do

```{admonition} Things to do
:class: seealso

- Dispose of the battery pack immediately if it has been subject to moisture and/or the case is eminently damaged. 
- In case of fire use a CO2 extinguisher.
- Store preferably in cool, dry and ventilated area subject to moderate temperature change.
- Storage at high temperatures (>50 C) should be avoided.

```
(db-opmanual-dtbattery-v2-donts)=
### Handling: things not to do

```{admonition} Things not to do
:class: warning

- Do not connect a charge voltage greater than 5V.
- Do not connect an external voltage source to the USB output ports.
- The battery must not be opened, destroyed or incinerated, since it may leak or rupture, releasing in the environment it's hermetically sealed chemicals.
- Do not short circuit terminals.
- Do not crush or puncture the battery, or immerse it in liquid.
- Do not place the battery near heating equipment, nor expose to direct sunlight for long periods.
```

<!--
### Battery modes

The Duckiebattery has several operation modes, the most relevant of which are described below.
-->

(db-opmanual-dtbattery-leds)=
### LED description
The battery has five LEDs on the top, used for indicating state of charge.

```{figure} ./chap_2_1_images/DB-C-DBatt_1.png
:width: 200px
:name: fig:DB-C-DBatt_1

LEDs indicate the state of charge of the Duckiebattery.
```
<!--
[comment]: <> (<div figure-id="fig:DB-C-DBatt_1" figure-caption="LEDs indicate the state of charge of the Duckiebattery.">)

[comment]: <> (     <img src="DB-C-DBatt_1.png" style='width: 25em' />)

[comment]: <> (</div>)
-->

```{note}
To see the battery state of charge, click _once_ on the button. The state of charge LEDs will stay on for 10 seconds and the battery set in `idle` state, " waking up" the battery.
```

```{figure} ./chap_2_1_images/DB-C-DBatt_2.png
:width: 200px
:name: DB-C-DBatt_2

Wake up the battery by pressing the button once.
```

<!--
[comment]: <> (<div figure-id="fig:DB-C-DBatt_2" figure-caption="Wake up the battery by pressing the button once.">)

[comment]: <> (     <img src="DB-C-DBatt_2.png" style='width: 30em' />)

[comment]: <> (</div>)
-->
(db-opmanual-dtbattery-v2-charging)=
### Charge the battery

After setting the battery in `idle` mode, charge it by connecting a 5V 2A power adapter. Note that using a higher amperage charger will not damage the unit. The LEDs will be flashing at 1 Hz, showing the battery is receiving charge.

```{figure} ./chap_2_1_images/DB-C-DBatt_3.png
:width: 200px
:name: fig:DB-C-DBatt_3

Charging the Duckiebattery.
```

When the battery's state of charge is particularly depleted (e.g., as soon as you receive the battery), the LEDs might be unresponsive for up to 30 minutes while receiving charge. 

<!--
[comment]: <> (<div figure-id="" figure-caption="Charging the Duckiebattery.">)

[comment]: <> (     <img src="DB-C-DBatt_3.png" style='width: 20em' />)

[comment]: <> (</div>)
-->

(db-opmanual-dtbattery-v2-protection-mode)=
### Battery protection mode

The battery is equipped with safety features to prevent damage to others and itself. In particular, it has dedicated hardware to protect its cell from low voltage discharge.

When a certain low cell voltage level is detected, the battery micro-controller, together with all other active components will be turned off, except the charger. When a Duckiebattery enters protection mode, it will look unresponsive.

Nonetheless, the charger will "trickle" charge the battery cell until it has reached a safe voltage level, exiting the battery protection mode.

The battery protection mode can last up to 30 minutes, during which the battery might not indicate a state of charge nor that it is actually being charged. This does not mean the battery is dead, just "hibernating".

(db-opmanual-dtbattery-v2-outputs)=
### USB outputs

The battery have two separate 5V 2A USB type A output, namely USB OUT-1 (a.k.a. the muscles) and USB OUT-2 (a.k.a. the brains).

```{figure} ./chap_2_1_images/duckiebattery-outputs.png
:width: 300px
:name: fig:DB-C-DBatt_4

Duckiebattery outputs behave differently.
```

<!--
[comment]: <> (<div figure-id="" figure-caption="">)

[comment]: <> (     <img src="" style='width: 25em' />)

[comment]: <> (</div>)
-->

- USB OUT-1: Connect this output to a non-sensitive power load, i.e., motor or LEDs. This output will experience short power drops when plugging and unplugging the charger cable.    

- USB OUT-2: this is an 5V 2A USB output, uninterrupted by the charging process or the status of USB OUT-1. This port should be connected to the computing unit (i.e., NVIDIA Jetson Nano or Raspberry Pi) to allow the unit not to restart when plugging or unplugging the charger of the battery.

(db-opmanual-dtbattery-v2-troubleshooting)=
### Troubleshooting

The most common fault is not related to the battery pack itself but the connection between the pack and the charger and/or the load.

```{note}
Always make sure the USB cable is not damaged and of good quality. Do not use a cable longer then 30cm. A faulty cable can cause excessive voltage drops between the battery pack and load, leading to low voltage issues.
```

<!--
The internal wires should be of at least 0.14 sqmm (or 26AWG).
-->

```{trouble}
My battery does not charge.
---
There can be several reasons why a charge is not being accepted. Below are the most common issue.

- The input voltage is too low or too high. Make sure you are apply 5V via the micro USB connector

- The battery is in battery protection mode and does not look like it's charging, but it is. Come back in >30 minutes and press the button once to enter `idle` mode.

- The battery is in a fault state. This can be caused by over temperature on the battery cell and/or its internal PCB. Leave the battery to cool down for 1h then attempt to charge it again.
```

```{trouble}
One or both USB output are not working
---
There can be several reasons why the USB output is not working. Below are the most common issue.

- The battery is not on `idle` mode. Press the battery button once.

- The battery is in battery protection mode. Remove all loads, put in charge and wait >30mins to have the battery exit protection mode. Then enter wake up the battery by pressing the button _once_.

- The USB output is in over current/temperature mode. Disconnect all loads, enter `idle` mode and let the battery rest for 30 minutes.

- A external voltage was applied to the USB (output) port(s). This is a big no no (refer to DO's and DONT's above). Disconnect all loads and enter `idle` mode.
```

(db-opmanual-dtbattery-v1)=
## The Duckie-power-bank 

The Duckie-power-bank (or Duckiebattery version 1) is the standard power source for Duckiebots in `DB18` and `DB19` configurations. Duckie-power-banks are easily recognizable:

```{figure} ./chap_2_1_images/duckiebattery-front.png
:width: 37em
:name: fig:duckiebattery-front

The Duckie Power Bank is the first version of the Duckiebattery, used in `DB18` and `DB19` Duckiebots.
```
<!--
[comment]: <> (<div figure-id="" figure-caption="">)

[comment]: <> (     <img src="duckiebattery-front.png" style='width: 37em' />)

[comment]: <> (</div>)
-->

(db-opmanual-dtbattery-v1-overview)=
### Overview

The Duckiebattery is equipped with 2 USB type A outputs (port A and B) and 1 Micro USB connector for charging.

```{figure} ./chap_2_1_images/duckiebattery-ports.png
:width: 37em
:name: fig:duckiebattery-ports

The Duckie Power Bank ports.
```
<!--
[comment]: <> (<div figure-id="" figure-caption="">)

[comment]: <> (     <img src="" style='width: 37em' />)

[comment]: <> (</div>)
-->

It also has 4 LEDs representing the state of charge. Push the button on the side of the battery pack to turn on the LEDs. The LEDs indicate the residual charge according to:

<!--
<div markdown="1">
 <col2 id='duckiebattery-charge' figure-id="tab:duckiebattery-charge" figure-caption="Duckiebattery LED charge indicators">
    <s>D1</s>                         <s>3-25%</s>
    <s>D2</s>                         <s>25-50%</s>
    <s>D3</s>                         <s>50-75%</s>
    <s>D4</s>                         <s>75-100%</s>
 </col2>
</div>
-->

```{list-table} Duckiebattery LED charge indicators
:header-rows: 1
:name: tab:duckiebattery-charge

* - LED
  - State of Charge
* - D1
  - 3-25%
* - D2
  - 25-50%
* - D3
  - 50-75%
* - D4
  - 75-100%
```


If D1 is flashing (0.5Hz) while not being charged, the battery pack is at a critical low charge (less than 3%).

(db-opmanual-dtbattery-v1-charging)=
### Charging

The battery pack is charged via the Micro USB port with a 5V supply. While charging, one of the LEDs will be flashing (0.5Hz) indicating where in the charge cycle it is.

```{note}
When the battery pack is connected to the charger, the output voltage of port A and B will turn off for around 280ms:
```

```{figure} ./chap_2_1_images/duckiebattery-voltage-profile.png
:width: 400px
:name: fig:duckiebattery-voltage-profile

The Duckie Power Bank output voltage drops when plugging in and removing teh charger.
```

<!--
[comment]: <> (<div figure-id="fig:duckiebattery-voltage-profile" figure-caption="The Duckie Power Bank ports">)

[comment]: <> (     <img src="duckiebattery-voltage-profile.png" style='width: 37em' />)

[comment]: <> (</div>)
-->


This is an unwanted effect which will cause the Raspberry Pi, if on, to reboot.

```{note}
likewise, when disconnecting the charger, the outputs will turn OFF for 20ms causing the Raspberry Pi to reboot as well.
```

Furthermore, while the Duckiebattery supports pass-through (both outputs A and B will function while the Duckiebattery is being charged), during charge the output voltage of port A and B will drop around 300mV which might cause an under voltage warring of the Raspberry Pi. This will put the Raspberry Pi in a throttling mode limiting its performance.

(db-opmanual-dtbattery-v1-discharging)=
### Discharging

The output ports A and B have an unloaded output voltage around 5.1V. To turn the outputs on simply plug in a load on port A/B, for example a Raspberry Pi and a Duckietown Hut, or push the button.

The output ports will automatically turn off if less than 100mA is being drawn.

To turn the outputs back on simply push the button or reconnect the USB connector.  

The combined output current is limited to 2.8A.

The battery capacity is 7.4Ah at 5V with an efficiency as follows:

<!--
| Load  &nbsp; &nbsp; |      Efficiency &nbsp; &nbsp;     |  Autonomy &nbsp; &nbsp; |
|----------|:-------------:|------:|
| 1 A |  91% | 6h 44m |
| 1.5 A |    88%   |   4h 33m |
| 2 A | 85% |    3h 9m |
| 2.5 A | 79% |    2h 21m |
-->

```{list-table} Duckie Power Bank discharge statistics
:header-rows: 1
:name: tab:duckie-power-bank-discharge

* - Load
  - Efficiency
  - Autonomy
* - 1 A
  - 91%
  - 6h 44m
* - 1.5 A
  - 88%
  - 4h 33m
* - 2 A
  - 85%
  - 3h 09m
* - 2.5 A
  - 79%
  - 2h 21m
```