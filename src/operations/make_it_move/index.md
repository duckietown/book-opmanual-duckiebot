```{seo}
:description: How to make a Duckiebot move.
:keywords: Duckietown, Duckiebot, remote control, keyboard control
```

(operation-make-it-move)=
# Operation - Make it Move

This section describes how to make your Duckiebot move.

(operation-make-it-move-keyboard-controller)=
## The Keyboard Controller

The easiest way to make your Duckiebot move is by using the `Keyboard Controller`.

```{figure} ../../_images/operations/keyboard_controller.png
:name: keyboard-controller

The `Keyboard Controller`.
```

To activate the `Keyboard Controller`, run:

    dts duckiebot keyboard_control ![DUCKIEBOT_NAME]

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: keyboard-controller-commands

* - Key
  - Function
* - <kbd>W</kbd>
  - Drive forwards
* - <kbd>S</kbd>
  - Drive backwards
* - <kbd>A</kbd>
  - Turn left
* - <kbd>D</kbd>
  - Turn right
* - <kbd>E</kbd>
  - Toggle the `Emergency Stop` switch
* - <kbd>F</kbd>
  - Toggle the `Autopilot` switch
* - <kbd>X</kbd>
  - Increase the `Gain`
* - <kbd>Z</kbd>
  - Decrease the `Gain`
* - <kbd>V</kbd>
  - Increase the `Trim`
* - <kbd>C</kbd>
  - Decrease the `Trim`
* - <kbd>Space</kbd>
  - Save the `Gain` and `Trim`
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

```{note}
The <kbd>F</kbd> key's function (`Autopilot`) requires software, such as the [lane following demo](demo-lane-following), to be running. For now, just try out the `Keyboard Controller` to get your Duckiebot moving.
```

(operation-make-it-move-troubleshooting)=
## Troubleshooting

```{trouble}
My Duckiebot does not move.
---
Before trying to use the `Keyboard Controller`, make sure that it is active by selecting it's window.
```

```{trouble}
The `Keyboard Controller` window is active but my Duckiebot still does not move. However, I can see messages being sent to my Duckiebot when looking at the `![DUCKIEBOT_NAME]/actuator/wheels/base/pwm` `DTPS` topic, after following [](operation-view-dtps-topics), and the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/components`) shows a red alert for the HUT.
---
If you have a HUT v3.1, re-flash it by following [](reflash-microcontroller).
```

```{trouble}
I have reflashed the HUT but my Duckiebot still does not move or moves in a jerky manner. Additionally, the ToF sensor and front bumper are not detected on the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/components`). I may also be having issues with the screen.
---
Disconnect the ToF sensor from the front bumper and use the long I2C cable, that originally connected the front bumper to the HUT, to connect the ToF sensor directly to that same HUT port. Finally, reboot your Duckiebot. This procedure bypasses a known multiplexer issue on some front bumpers that can cause other issues with the HUT.
```

```{trouble}
I have  connected the ToF sensor directly to the same HUT port that the front bumper was originally connected to and rebooted my Duckiebot but it still does not move.
---
Make sure that the `duckiebot-interface` container is running by opening the [Portainer interface](dashboard-portainer) or by running:

    `docker -H ![DUCKIEBOT_NAME].local ps`

The exact name of the container will depend on your Duckiebot's version. If you do not see the `duckiebot-interface` container, update your Duckiebot by running:

    `dts duckiebot update ![DUCKIEBOT_NAME]`
```

```{trouble}
When I press the <kbd>W</kbd> key, my Duckiebot moves backwards.
---
If you have a `DB17` or `DB18`, revert the polarities (`+` and `-`) of the cables that go to the motor driver (HUT) for both motors.
```
