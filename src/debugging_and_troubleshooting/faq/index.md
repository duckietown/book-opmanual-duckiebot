(troubleshooting-faq)=
# Duckiebot FAQ Guide

This FAQ page collects common roadblocks you might run into when setting up your Duckietown environment and 
operating your Duckiebot.

Each symptom and resolution are also available on the pages they relate to throughout the manual, so be sure to watch for troubleshooting 
tip and carefully complete checkpoints as you progress.

If you don't find the solutions you need in this book, be sure to first search the Duckietown Stack 
Overflow and Slack communities for previous answers, then post your own question following the support guidelines on 
Slack.

(boot-faq)=
## FAQs: Booting your Duckiebot

```{trouble}
I pressed the power button on top to boot my Duckiebot but nothing happened.
---
Power on your Duckiebot using the button on the side of the Duckiebattery.  The top button is only for powering off. 
 You can also learn more about how to handle your Duckiebot in [](handling-duckiebot-db21).
```

```{trouble}
My Duckiebot does not appear to boot after pressing the power button on the battery. I don't see a green light on 
the HUT or the Jetson Nano.
---
Refer back to [](assembling-duckiebot-db21j), and check each of your cable connections.  Confirm the start and end 
port of each power cable from the battery.  The battery must be charged fully as shown in the first assembly step.
```

```{trouble}
My Duckiebot is getting power but does not appear to be booting. The Wifi dongle is not blinking.
---
Make sure you flashed the SD card following the instructions in [](setup-duckiebot-sd-card).
```

```{trouble}
My Duckiebot is getting power but does not appear to be booting. The Wifi dongle is not blinking.
---
Make sure that you correctly specified the model of your Duckiebot when initializing the SD card.

If you have a Duckiebot with a 2GB Jetson Nano - the model is DB21M

If you have a Duckiebot with a 4GB Jetson Nano - the model is DB21J

If you are not using a Jetson Nano, the model is the model of your Duckiebot (ex. DB19 or DBR4)
```

```{trouble}
The Duckiebot screen does no turn on even though it shows up in `dts fleet discover` and the dashboard is accessible.
 The ToF and front bumper are not detected on the dashboard Components page.
---
Disconnect the ToF sensor from the front bumper and use the long cable that originally connected the front bumper to 
the HUT to connect the ToF sensor directly to that same HUT port. Then reboot. This bypasses a known multiplexer 
issue on some 
bumpers.
```

```{trouble}
My Duckiebot appears to be booted and the screen is on, but I can't see it using `dts fleet discover`.
---
Your Duckiebot must be connected to the same network as the computer you are using to run the `dts` commands.  Check 
the [networking section](duckiebot-network) of the book to see if your network is set up correctly.
```

```{trouble}
I am not sure whether my Duckiebot is properly initialized.
---
As long as the `fleet discover` tool shows ready, your Duckiebot should be ready. 
You can also visit the dashboard to confirm that the Duckiebot is serving its status. 
Generally as long as you see the Duckiebot dashboard is up, your Duckiebot should be correctly initialized.
```

```{trouble}
I see a permissions error when trying to access the Duckiebot dashboard: `Directory '/data/config/permissions' 
cannot be written`.
---
* Take the sd card from your robot (press in once to release the spring, then remove)
* Put it in your laptop using the adapter that came with the card
* Navigate to the root of the card in your terminal. Most OS have an option to right click on the drive when it 
appears on your desktop or in the sidebar and select a "open in terminal", "new terminal at folder", or similar
* Run chmod 777 /data/config/permissions
* Eject the drive, place back in the Duckiebot, and power back up
```

(operation-faq)=
## FAQs: Operating your Duckiebot

```{trouble}
The power button on top does not shut off the Duckiebot.
---
The power button needs to be held for three seconds and then released.  If this still does not work, run `dts 
duckiebot update <your_robot>` and then use `dts duckiebot reboot <your_robot>`.  You may also need to re-flash your 
`HUT` following the procedure described in [](reflash-microcontroller) if you have not already.
```

```{trouble}
My Duckiebot has a very low battery charge and is stuck in a boot cycle.
---
Unplug all cables from the HUT except port # that is used to charge the battery.  Allow the battery to charge for at 
least 5 hours before plugging all cables back in their nominal positions.
```

```{trouble}
When using the keyboard control GUI, I can see the commands being sent to the Duckiebot (e.g., through the 
**Dashboard > Mission Control**), but 
the Duckiebot does not move. My **Dashboard > Robot > Components** page shows a red alert for the `HUT`.
---
If you have a `HUT` v3.15 you will stumble on this problem the first time you try to move your Duckiebot. Re-flash your `HUT` following the procedure described in [](reflash-microcontroller).
```

```{trouble}
I have reflashed the HUT but the joystick commands still do not work or the Duckiebot operates in a jerky manner.  
Additionally, the ToF sensor and front bumper are not detected on the dashboard Components page. I may also be 
having issues with the screen.
---
Disconnect the ToF sensor from the front bumper and use the long cable that originally connected the front bumper to 
the HUT to connect the ToF sensor directly to that same HUT port. Then reboot. This bypasses a known multiplexer 
issue on some bumpers that can cause other HUT misbehaviors.
```

```{trouble}
I'm still having a software issue that the Duckietown team has pushed a new fix for according to StackOverflow.
---
You can pull the latest images to your Duckiebot by running `dts duckiebot update <duckiebot_name>`.  This is always 
the correct way to reset your Duckiebot's containers.  You will never need to reflash the SD card to get updates.
```
