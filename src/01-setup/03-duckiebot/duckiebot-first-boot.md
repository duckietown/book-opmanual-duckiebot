```{seo}
:description: Guide on turning on your Duckiebot for the first time. During the first boot, the Duckiebot completes its initialization procedure. 
:keywords: Duckietown, Duckiebot, first boot, booting up a Duckiebot
```

(duckiebot-boot)=
# Setup - Duckiebot First Boot

```{needget}
- A flashed Duckiebot SD card: [](setup-db-sd-card-flashing-intro)
- A Duckiebot of the same model chosen during the SD card flashing procedure
- A charged battery (>50%)
---
- An online (successfully initialized) Duckiebot
- (if network is correctly configured) A Duckiebot connected to the network
```

## You are now ready to boot up your Duckiebot

Insert the initialized SD card into your Duckiebot's Jetson Nano until your feel a "click". Then, push the button on the 
battery to power up the Duckiebot. 


```{vimeo} 527364179
:alt: Duckiebot first boot
```

```{warning}
Be sure your Duckiebattery is well charged before attempting to boot the Duckiebot for the first time.

The external power supply might not be able to provide sufficient current if the battery is low, causing the on-board 
computer to reboot. Should that happen during the first boot, you will likely have to burn the SD card again.
```


(monitor-first-boot)=
## Monitoring the First Boot

Make sure your desktop or laptop computer is connected to the same Wi-Fi network the Duckiebot was instructed to connect to.

Then open a terminal and run:

``` 
dts fleet discover
```

The command above will show a list of all the Duckiebots reachable on your local network.  For each Duckiebot, `dts fleet discover` will also show the model that was used to flash the SD card, the hostname of your robot, and a status indicator.

Leave this tool open, it will refresh automatically every second, so there is no need to manually restart it.

Within a few minutes of powering up the robot with the SD card in, your Duckiebot will appear in the list with status **Booting**.  If it does not appear within 5 minutes, check out the Troubleshooting guide at the end of this page.

```{figure} ../../_images/setup/handling/fleet_discover.png
:name: fig:fleet-discover
:width: 85%

Output of 'dts fleet discover'
```

```{attention}
During the first boot, the robot will automatically reboot several times. Wait for the "Status" column to read "Ready" and turn solid green.
```

## Software and Hardware Updates

Once the status of your Duckiebot is `Ready`, you are ready to update your Duckiebot. The software update is required now, while the hardware update is conditional and also can be carried out later.

### Duckiebot Software Update

It is good practice to keep your Duckiebot's software stack up to date with the latest code by following: [](ops-db-update).

    dts duckiebot update ROBOT_NAME

(confirm-first-boot)=
## Confirming the First Boot

Once the Duckiebot is `Ready` and `Updated` (software), you are ready to access your Duckiebot's Dashboard and perform the first login [Dashboard setup](duckiebot-dashboard-setup).

<!--
Open your browser and visit the
URL `http://HOSTNAME.local/`. You will see a page similar to the following,

```{figure} ../../_images/compose_first_setup.png
:name: fig:compose_first_setup

Duckiebot's dashboard first setup page
```

This is the dashboard of your Duckiebot. The Dashboard is built using a
framework called \\compose\\. You configure it in in [](duckiebot-dashboard-setup).

If you can't access the dashboard, check out the Troubleshooting guide at 
the end of this page.
-->

<!--
(setup-duckiebot-reboot)=
## Powering off the Duckiebot

```{warning}
Do not test these commands before the Duckiebot has completed its first boot. 
If the Duckiebot gets rebooted/shutdown while the first boot has not finished, 
the Duckiebot might become unreachable and you will have to reflash the SD card.
```

To turn off your Duckiebot, use the command,

    dts duckiebot shutdown HOSTNAME

The shutdown procedure can take up to `20` seconds.

To reboot your Duckiebot, use the command,

    dts duckiebot reboot HOSTNAME

You will learn more about how to handle your Duckiebot in [](how-to-handle-a-duckiebot-db21).
-->

<!--
### (optional) HUT Microcontroller Update

We call Duckiebot "HUT" (not a typo) the electronic board that connects to the GPIO pins of the onboard computer. 

```{warning}
It is not necessary to run this procedure after the first boot. We add this link here for completeness and to inform you of the existence of a microcontroller on the HUT.
```

The Duckiebot HUT connects to various electronics beyond the Duckiebot onboard computer, like motors and LEDs.

If facing challenges with moving your Duckiebot or controlling the LEDs, it is possible that [reflashing the Duckiebot's HUT](reflash-microcontroller) might address your issues.
-->

(duckiebot-first-boot-troubleshooting)=
## Troubleshoot - First Boot

```{trouble}
I pressed the power button on top but nothing happened.
---
Power on your Duckiebot using the button on the side of the Duckiebattery.  The top button is only for powering off. 
 You can also learn more about how to handle your Duckiebot in [](how-to-handle-a-duckiebot-db21).
```

```{trouble}
My Duckiebot does not appear to boot after pressing the power button on the battery. I don't see a green light on 
the HUT or the Jetson Nano.
---
Refer back to [](assembly-instructions-db21j), and check each of your cable connections.  Confirm the start and end 
port of each power cable from the battery.  The battery must be charged fully as shown in the first assembly step.
```

```{trouble}
My Duckiebot is getting power but does not appear to be booting. The Wi-Fi dongle is not blinking.
---
Make sure you flashed the SD card following the instructions in [](setup-db-sd-card-flashing-intro).
```

```{trouble}
My Duckiebot is getting power but does not appear to be booting. The Wi-Fi dongle is not blinking.
---
Make sure that you correctly specified the model of your Duckiebot when initializing the SD card.

If you have a Duckiebot with a 2GB Jetson Nano - the model is `DB21M`

If you have a Duckiebot with a 4GB Jetson Nano - the model is `DB21J`

If you are not using a Jetson Nano, the model is the model of your Duckiebot (e.g., `DB19` or `DBR4`)
```

```{trouble}
The Duckiebot screen does no turn on even though it shows up in `dts fleet discover` and the dashboard is accessible.
 The time of flight (ToF) sensor and front bumper are not detected on the Dashboard Components page.
---
Disconnect the ToF sensor from the front bumper and use the long cable that originally connected the front bumper to 
the HUT to connect the ToF sensor directly to that same HUT port. Then reboot. This bypasses a known multiplexer 
issue affecting some front bumpers.
```

```{trouble}
My Duckiebot appears to be booted and the screen is on, but I can't see it using `dts fleet discover`.
---
Your Duckiebot must be connected to the same network as the computer you are using to run the `dts` commands.  Check 
the [networking section](setup-duckiebot-network) of the book to see if your network is set up correctly.
```

```{trouble}
I am not sure whether my Duckiebot is properly initialized.
---
As long as the `fleet discover` tool shows ready, your Duckiebot should be ready. 
You can also visit the dashboard to confirm that the Duckiebot is serving its status. 
Generally as long as you see the Duckiebot dashboard is up, your Duckiebot should be correctly initialized.
```