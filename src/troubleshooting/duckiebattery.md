<<<<<<< HEAD
<<<<<<< Updated upstream
=======
# Duckiebattery

>>>>>>> Stashed changes
=======
# Duckiebattery

>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
```{seo}
:description: The Duckiebattery.
:keywords: Duckietown, Duckiebot, Duckiebattery
```

<<<<<<< HEAD
<<<<<<< Updated upstream
(duckiebattery)=
# Duckiebattery

This chapter describes the Duckiebattery.

```{needget}
* Completed [](handling) up to [](how-to-turn-your-duckiebot-off).
=======
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
This chapter describes the Duckiebattery.

```{needget}
* Completed [](../setup/handling.md) up to [](handling-how-to-turn-your-duckiebot-off).
<<<<<<< HEAD
>>>>>>> Stashed changes
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
* A [Duckiebattery](db-opmanual-dtbattery-v2).
---
Knowledge on the Duckiebattery.
```

```{note}
Make sure to follow [](duckiebattery-things-to-do) and [](duckiebattery-things-to-not-do).
```

(duckiebattery-introduction)=
## Introduction

```{figure} ../_images/troubleshooting/duckiebattery/DB-C-DBatt_real2.jpg
:name: fig:DB-C-DBatt_real
:width: 30em

The Duckiebattery.
```

The Duckiebattery is a programmable and smart lithium-ion battery designed for Duckiebots.
It allows your Duckiebot to diagnose the Duckiebattery's state (e.g., charge) and send shutdown requests via software.

(duckiebattery-technical-specifications)=
## Technical specifications

The Duckiebattery has:

* A capacity of `10 Ah` at `3.7 V`.
* `5 V` charging via Micro USB at up to `2 A`.
* A `5 V` output via two USB type A ports at up to `4 A` (combined), with a maximum of `2.5 A` on a single port.
* A `0-100%` charge time of around `5 h`.
* A `0-90%` charge time of around `4 h` with a `2 A` power supply.
* A mass of `189 g` (fully charged).

```{caution}
Lithium-ion batteries are potentially dangerous and must be handled with care.
```

(duckiebattery-things-to-do)=
## Things to do

```{admonition} Things to do
:class: seealso

* Dispose of the Duckiebattery immediately if it has been exposed to moisture and/or eminently damaged.
* Use a CO2 extinguisher if the Duckiebattery combusts.
* Store the Duckiebattery in a cool, dry and ventilated environment, subject to moderate temperature changes.
* Avoid storing the Duckiebattery in high temperature (greater than `50 °C`) environments.
```

(duckiebattery-things-to-not-do)=
## Things not to do

```{admonition} Things not to do
:class: warning

* Do not connect a charge voltage greater than `5 V` to the Duckiebattery.
* Do not connect an external voltage source to the Duckiebattery's output USB ports.
* Do not open, destroy or incinerate the Duckiebattery, as it may leak or rupture, releasing its hermetically sealed chemicals into the environment.
* Do not short circuit the Duckiebattery's terminals.
* Do not crush or puncture the Duckiebattery.
* Do not immerse the Duckiebattery in liquid.
* Do not place the Duckiebattery near heating equipment or expose it to direct sunlight for prolonged periods.
```

(duckiebattery-leds)=
## LEDs

The Duckiebattery has five LEDs, which are used to indicate its state of charge.

```{figure} ../_images/troubleshooting/duckiebattery/DB-C-DBatt_1.png
:name: fig:DB-C-DBatt_1

LEDs indicating the Duckiebattery's state of charge.
```

```{note}
To see the Duckiebattery's state of charge, click its button **once**.
The LEDs will stay on for `10 s` and the Duckiebattery will be set to `idle` mode, "waking up" the Duckiebattery.
```

```{figure} ../_images/troubleshooting/duckiebattery/DB-C-DBatt_2.png
:name: fig:DB-C-DBatt_2

The Duckiebattery turning on after pressing its button.
```

(duckiebattery-charging)=
## Charging

After setting the Duckiebattery to `idle` mode, charge it by connecting it to a `5 V` `2 A` charger.
The LEDs will flash at `1 Hz`, showing that the Duckiebattery is receiving charge.

```{note}
Using a higher amperage charger will not damage the Duckiebattery.
```

```{note}
When the Duckiebattery's state of charge is particularly low (e.g., when you first receive the Duckiebattery), the LEDs may be unresponsive for up to `30 min` while receiving charge.
```

```{figure} ../_images/troubleshooting/duckiebattery/DB-C-DBatt_3.png
:name: fig:DB-C-DBatt_3

Charging the Duckiebattery.
```

(duckiebattery-protection-mode)=
## Protection mode

The Duckiebattery is equipped with safety features to prevent damage to itself and others.
In particular, it has dedicated hardware to protect its cells from low-voltage discharge.

When a certain low cell voltage level is detected, the Duckiebattery's active components, such as its microcontroller, minus the charger will be turned off.
When the Duckiebattery enters `protection` mode, it will look unresponsive.
Nonetheless, the charger will "trickle" charge the Duckiebattery cell until it has reached a safe voltage level, after which the Duckiebattery will exit `protection` mode.

The Duckiebattery's `protection` mode can last up to `30 min`, during which it may not indicate a state of charge nor that it is being charged.

```{note}
This does not mean that the Duckiebattery is dead.
It is just "hibernating".
```

(duckiebattery-usb-outputs)=
## USB outputs

The Duckiebattery has two `5 V` `2 A` USB type A outputs:

* `OUT-1` (the "muscles").
* `OUT-2` (the "brains").

`OUT-1` can be connected to a non-sensitive power load (e.g., motor, LED, etc.).
It will experience short power drops when plugging the charging cable in or out.

`OUT-2` is a `5 V` `2 A` USB output, uninterrupted by the charging process or the status of `OUT-1`.
It should be connected to the on-board computer, to prevent the Duckiebattery from restarting when plugging the charging cable in or out.

```{figure} ../_images/troubleshooting/duckiebattery/duckiebattery-outputs.png
:name: fig:DB-C-DBatt_4

The Duckiebattery's outputs behave differently.
```

(duckiebattery-update)=
## Update

To update the Duckiebattery:

1. Run `pipx upgrade duckietown-shell`.
2. Run `dts update`.
3. Run `dts desktop update`.
4. Run `dts fleet discover` and verify that your Duckiebot is `Ready`.
5. Run `dts duckiebot update DUCKIEBOT_NAME`.
6. Run `dts duckiebot battery info DUCKIEBOT_NAME` and verify that `percentage` is greater than `15`.
7. Run `dts duckiebot battery upgrade DUCKIEBOT_NAME` and follow the instructions. If prompted to "double-click" the Duckiebattery's button, *quickly* press the Duckiebattery's button **twice**.
8. (optional) If the display shows "NoBT", press the Duckiebattery's button **once** and reboot your Duckiebot.
9. Run `dts duckiebot battery check_firmware DUCKIEBOT_NAME` and verify that `version` is greater than or equal to `2.0.2`.

````{attention}
If the output of step 7 is `SAM-BA operation failed INFO:UpgradeHelper:An error occurred while flashing the battery. ERROR:dts:The battery reported the status 'GENERIC_ERROR'`, run:

```shell
dts duckiebot battery upgrade --force DUCKIEBOT_NAME
```

Otherwise, if the output of the step 7 is any other error message, press the Duckiebattery's button **once**, reboot your Duckiebot and try again.
````

```{note}
You can verify that the Duckiebattery related software is running correctly by checking whether the display reacts to different charging states when plugging the charging cable in or out.
```

(duckiebattery-troubleshooting)=
## Troubleshooting

```{note}
The most common fault is not related to the Duckiebattery itself but the connection between it and the charger and/or the load.
```

```{note}
Make sure that the charging cable is not damaged and is of good quality.
Do not use a charging cable longer than `30 cm`.
A faulty cable can cause excessive voltage drops between the Duckiebattery and load, leading to low voltage issues.
```

```{trouble}
The Duckiebattery does not look like it is charging.
---
There could be several reasons why the Duckiebattery would not look like it is charging:

* The input voltage may be too low/high (make sure to apply `5 V` via the Micro USB connector).
* The Duckiebattery is in `protection` mode (wait for around `30 min` and then press its button **once**).
* The Duckiebattery is in a fault state, which could be caused by a cell and/or its internal PCB being overheated (unplug the charging cable from the charger, wait for around `1 h` and then plug the charging cable back into the charger).
```

```{trouble}
One or both of the USB output ports are not working.
---
There could be several reasons why a USB output port would not be working:

* The Duckiebattery is not in `idle` mode (press its button **once**).
* The Duckiebattery is in `protection` mode (disconnect all loads, plug the charging cable into a charger, wait for around `30 min` and then press its button **once**).
* The USB output port is in `overcurrent`/`overtemperature` mode (disconnect all loads, press the Duckiebattery's button **once** and then wait for around `30 min`).
* An external voltage was applied to the USB output port (disconnect all loads and then press the Duckiebattery's button **once**).
```
