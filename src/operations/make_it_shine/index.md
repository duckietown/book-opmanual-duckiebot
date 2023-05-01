(led-control)=
# Operation - Make it Shine

This section describes how control the LEDs on your Duckiebot.

Duckiebots have four LEDs, positioned similarly to the head and tail lights on a car.

```{figure} ../../_images/operations/leds_layout.png
:name: leds_layout

A duckiebot with the LEDs shining white and a diagram with arrows indicating the front and rear LEDs.
```

LEDs as actuators on a Duckiebot can be used for many purposes, including

* Indicating what mode or mission the Duckiebot is running
* Communicating state changes in the controller
* Signaling upcoming turns or other navigation plans
* Expressing character and personality
* And simply lighting the driving environment

(make-it-shine_shell)=
## LED control

You can update the LEDs on your Duckiebot manually by bringing up the LED Widget using the `led_control` command provided by the Duckietown Shell.

Open a terminal and run:

    dts duckiebot led_control ![DUCKIEBOT_NAME]

```{attention}
For all operation commands that use the Duckiebot's name - replace `![DUCKIEBOT_NAME]` with just the Duckiebot's `hostname`, do not include `.local` part that you used previously to access the dashboard.
```

After startup, the `led_control` command will open an interface window. Make sure the window is active by selecting it, and press the buttons to update the color and intensity of your Duckiebot's LEDs.

```{figure} ../../_images/operations/led_widget.png
:name: led_widget

The LED control interface
```

## Troubleshooting

```{trouble}
When I press the buttons, the LEDs do not update. My **Dashboard > Robot > Components** page shows a red alert for the `HUT`.
---
If you have a `HUT` v3.1 you will stumble on this problem the first time you try to move your Duckiebot. Re-flash your `HUT` following the procedure described in [](reflash-microcontroller).
```

```{trouble}
I have reflashed the HUT but the led commands still do not work.  
Additionally, the ToF sensor and front bumper are not detected on the dashboard Components page. I may also be 
having issues with the screen and joystick control.
---
Disconnect the ToF sensor from the front bumper and use the long cable that originally connected the front bumper to 
the HUT to connect the ToF sensor directly to that same HUT port. Then reboot. This bypasses a known multiplexer 
issue on some bumpers that can cause other HUT misbehaviors.
```

```{trouble}
I checked the two troubleshooting issues above, and my Duckiebot still doesn't respond.
---
Check that the `duckiebot-interface` container is running

Open [the Portainer interface](dashboard-portainer) and check the running containers. You should see one that has a name that contains `duckiebot-interface` (exact container name will depend on your robot version).

You can also determine this by running:

    `docker -H ![ROBOT_NAME].local ps`

and look at the output to find the `duckiebot-interface` container and verify that it is running.

If you don't see the container, your base image is out of date - update your Duckiebot with the command

    `dts duckiebot update ![ROBOT_NAME]`
```
