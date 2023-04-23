(duckiebot-boot)=
# Setup - Booting the Duckiebot

```{needget}
- A flashed Duckiebot SD card
- A Duckiebot of the same model chosen during the SD card flashing procedure
- A fully charged battery
---
A Duckiebot successfully booted up and connected to the WiFi network.
```


## You are now ready to boot up your Duckiebot!

Insert the SD card as shown in the video below into your robot and push the button on the 
battery to power up the Duckiebot. While the video shows the procedure being performed on 
a `DB21M` robot, this procedure is the same on all Duckietown robot models.

```{vimeo} 527364179
```

```{warning}
Be sure your Duckiebattery was fully charged as shown in the assembly steps before 
attempting to boot.

The external power supply might not be able to provide sufficient current if the battery is low, causing the on-board 
computer to reboot. Should that happen during the first boot, you will likely have to 
burn the SD card again.
```


(monitor-first-boot)=
## Monitoring the First Boot

Make sure your desktop or laptop computer is connected to the same WiFi network the Duckiebot
was instructed to connect to.
Then open a terminal and run the following command,

``` 
dts fleet discover
```

The command above will show a list of all the Duckiebots
reachable on your local network. Leave this tool open, it will refresh automatically every
second, so there is no need to manually restart it.

Within a few minutes of powering up the robot with the SD card in, your Duckiebot will appear
in the list with status **Booting**.  If it does not appear within 5 minutes, check out the Troubleshooting guide at 
the end of this page.

```{figure} ../../_images/fleet_discover.jpg
:name: fig:fleet-discover

Output of 'dts fleet discover'
```

During the first boot, the robot will automatically reboot several times.
Wait for the "Status" column to read "Ready" and turn solid green.

(confirm-first-boot)=
## Confirming the First Boot

You are now ready to access your Duckiebot's Dashboard.
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

You will learn more about how to handle your Duckiebot in [](handling-duckiebot-db21).

(duckiebot-first-boot-troubleshooting)=
## Troubleshoot - First Boot

```{trouble}
The red LED on the Raspberry Pi is OFF.
---
Press the button on the side of the battery ([](troubleshooting-battery-button)).
```

```{trouble}
The Raspberry Pi has power but it does not boot.
---
[Initialize the SD card](setup-duckiebot-sd-card) if not done already. If problem persists, ask on 
[Stack Overflow](https://stackoverflowteams.com/c/duckietown).
```


```{trouble}
I cannot ping the Duckiebot.
---
Check the [networking section](duckiebot-network) of the book to see if your network is set up correctly.
```


```{trouble}
I am not sure whether the Duckiebot is properly initialized.
---
As long as the fleet discover tool shows ready, your Duckiebot should be ready. 
You can also visit `http://HOSTNAME.local/docker/` to see all the container status. 
Generally as long as you see the Duckiebot web UI is up, your Duckiebot should be correctly initialized.
```


```{trouble}
**`DB18` and `DB19` only**: The LEDs light up in a variety of colors when the battery is plugged in for the first time.
---
The LEDs of the (`DB18` and `DB19`) Duckiebot should light up in white as soon as you power the Duckiebot. 
If the LEDs turn on and shine in any different color than white, probably the code on the microcontroller 
is corrupted. You can reflash it using the procedure in [](reflash-microcontroller).
```


```{trouble}
On first boot, the lights of the Duckiebot do not turn white (might be blue).
---
Run the following commands `dts duckiebot update HOSTNAME`      
```

