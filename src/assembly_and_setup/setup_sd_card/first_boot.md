(duckiebot-boot)=
# Booting the Duckiebot

```{needget}
- A flashed Duckiebot SD card
- A Duckiebot of the same model chosen during the SD card flashing procedure
- A fully charged battery
---
A Duckiebot successfully booted up and connected to the WiFi network.
```


Now insert the SD card as shown in the video below into your robot and push the button on the 
battery to power up the Duckiebot. While the video shows the procedure being performed on 
a `DB21M` robot, this procedure is the same on all Duckietown robot models.

```{vimeo} 527364179
```

```{warning}
Unless you are using a Duckiebattery (available in the `DB21M` and `DB21J` Duckiebots), 
don't charge the battery while you are doing the initialization 
(or in general when the Duckiebot is turned on). 
The external power supply might not be able to provide sufficient current, causing the on-board 
computer to reboot. Should that happen during the first boot, you will likely have to 
burn the SD card again.
```


(monitor-first-boot)=
## Monitoring the First Boot

Make sure your desktop or laptop computer is connected to the same WiFi network the Duckiebot
was instructed to connect to.
Open a terminal and run the following command,

``` 
dts fleet discover
```

The command above will show a list of all the Duckiebots
reachable on your local network. Leave this tool open, it will refresh automatically every
second, so there is no need to manually restart it.

Within a few minutes of powering up the robot with the SD card in, your Duckiebot will appear
in the list with status **Booting**.

The list will look like the following.

```{figure} ../../_images/fleet_discover.jpg
:name: fig:fleet-discover

Output of 'dts fleet discover'
```

During the first boot, the robot will automatically reboot several times.
Wait for the "Status" column to read "Ready" and turn solid green.
You are now ready to access your Duckiebot's Dashboard.
Open your browser and visit the
URL `http://HOSTNAME.local/`. You will see a page similar to the following,

```{figure} ../../_images/compose_first_setup.png
:name: fig:compose_first_setup

Duckiebot's dashboard first setup page
```

This is the dashboard of your Duckiebot. The Dashboard is built using a
framework called \\compose\\. You will see how to configure it in [](duckiebot-dashboard-setup).


(setup-duckiebot-ssh)=
## SSH to the Duckiebot

Next, let us try and log in onto our robot using the SSH (Secure Shell) protocol. We can do
so by running the command,

    ssh duckie@HOSTNAME.local

The default password is `quackquack`.


(setup-duckiebot-reboot)=
## Rebooting the Duckiebot

```{warning}
Do not test these commands before the Duckiebot has completed its first boot. 
If the Duckiebot gets rebooted/shutdown while the first boot has not finished, 
the Duckiebot might become unreachable and you will have to reflash the SD card.
```

To reboot your Duckiebot, use the command,

    dts duckiebot reboot HOSTNAME


(setup-duckiebot-poweroff)=
## Turn off the Duckiebot 

To turn off your Duckiebot, use the command,

    dts duckiebot shutdown HOSTNAME

The shutdown procedure can take up to `20` seconds.

```{warning}
If you disconnect the power before shutting down properly using `shutdown`,
the system might get corrupted.
```

```{note}
If you have a Duckiebot that is powered by the official [Duckiebattery](db-opmanual-dtbattery-v2),
e.g., `DB21M`, this procedure will shutdown the battery as well.
This means that you do not need to manually disconnect any component from the battery. 
Learn more about handling the Duckiebattery in [](handling-duckiebot-db21m).

If you **DO NOT** have a Duckiebot that is powered by the official Duckiebattery, 
disconnect the USB cable from the battery.
```

```{warning}
If you disconnect frequently the cable at the computational unit's end, you might damage the port.
```
