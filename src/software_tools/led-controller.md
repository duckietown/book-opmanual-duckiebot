```{seo}
:description: The LED Controller.
:keywords: Duckietown, Duckiebot, LED Controller
```

(led-controller)=
# LED Controller

This chapter describes the `LED Controller`.

```{needget}
Completed [](dtps).
---
Knowledge on the `LED Controller`.
```

## Introduction

Duckiebots have four LEDs, positioned similarly to the head and tail lights on a car.

```{figure} ../_images/software_tools/led_controller/leds_layout.png
A Duckiebot with the LEDs shining white (left) and a diagram with arrows indicating the front and back LEDs (right).
```

LEDs as actuators on a Duckiebot can be used for many purposes, including but not limited to:

* Indicating what mode or mission the Duckiebot is running.
* Communicating state changes in the controller.
* Signaling upcoming turns or other navigational plans.
* Expressing character and personality.
* Lighting the driving environment.

An easy way to control your Duckiebot's LEDs is by using the `LED Controller`.

```{figure} ../_images/software_tools/led_controller/led_controller.png
The `LED Controller`.
```

To open the `LED Controller`, run:

```shell
dts duckiebot led_control DUCKIEBOT_NAME
```

To control your Duckiebot's LEDs, use the buttons and sliders to change their colors and intensities, respectively.

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: table:led-controller-commands

* - Key
  - Function
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

```{note}
The color dropper tool is not operational yet.
```

## Troubleshooting

```{trouble}
I can see messages being sent to my Duckiebot when looking at the `DUCKIEBOT_NAME/actuator/lights/base/pattern` `DTPS` topic, after following [](dtps), but the LEDs do not update and the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components`) shows a red alert for the HUT.
---
If you have a HUT v3.1, follow [](hut).
```

```{trouble}
My Duckiebot's LEDs do not update and I cannot see messages being sent to my Duckiebot when looking at the `DUCKIEBOT_NAME/actuator/lights/base/pattern` `DTPS` topic, after following [](dtps).
---
Contact support.
```

```{trouble}
I have re-flashed the HUT but the LEDs still do not update. Additionally, the ToF sensor and front bumper are not detected on the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components`). I may also be having issues with the screen.
---
Disconnect the ToF sensor from the front bumper and use the long I2C cable, that originally connected the front bumper to the HUT, to connect the ToF sensor directly to that same HUT port. Finally, reboot your Duckiebot. This procedure bypasses a known multiplexer issue on some front bumpers that can cause other issues with the HUT.
```

```{trouble}
I have connected the ToF sensor directly to the same HUT port that the front bumper was originally connected to and rebooted my Duckiebot but the LEDs still do not update.
---
Make sure that the `duckiebot-interface` container is running by checking the `Portainer` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page portainer`) or by running:

    `docker -H DUCKIEBOT_NAME.local ps`

The exact name of the container will depend on your Duckiebot's version. If you do not see the `duckiebot-interface` container, update your Duckiebot by running:

    `dts duckiebot update DUCKIEBOT_NAME`
```
