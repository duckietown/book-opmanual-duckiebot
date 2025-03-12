```{seo}
:description: It looks like a toy but it is a professional robot. Learn how to handle a Duckiebot (DB21J4) - power on, shutdown, ssh, etc.
:keywords: Duckietown, Duckiebot, handling, power on, power off, shutdown, soft shutdown, hard shutdown, ssh
```

(handling-duckiebot-db21)=
# Handling - Duckiebot `DB21`

```{needget}
- An assembled `DB21` robot (e.g., `DB21M`, `DB21J`);
- An initialized `DB21` with **firmware version 1.2.2 or newer**. [Check your current firmware version](duckiebot-dashboard-use) before proceeding.
---
Knowledge on standard protocols to turn on, turn off, charge, and update the Duckiebattery software version on a `DB21` robots;
```

```{note}
The box above contains important information on the requirements. Make sure to read and follow them before proceeding.
```

```{note}
In this manual, we use `DB21` to refer to any version of the Duckiebot with prefix `DB21`, such as, `DB21J`, `DB21M`, etc.
```

(tutorial-handling-db21-video)=
## Duckiebot `DB21` handling tutorial video

```{vimeo} 527038785
```

(howto-db21-charge)=
## How to charge a `DB21`

To charge your Duckiebot, follow these steps:

- Plug in the charging cable to the free microUSB port on the `HUT`.

Note: to minimize mechanical stress on the `HUT` we recommend plugging in the charging cable once, 
and leaving the USB port end free to plug and unplug from charging instead. 
You can arrange the cable under the `DB21` top plate during operations for cable management.

- Plug in the charger to a 5V 2A source.
  ```{note}
  the battery can draw up to 2A. Feeding a higher amperage will not be a problem, but wrong voltage 
  will send the battery in [protection mode](db-opmanual-dtbattery-v2-protection-mode).
  ```

- If the Duckiebot is turned on when charging, a battery charge indicator will appear on the top right 
  of the screen. If the Duckiebot is turned off, the LEDs will turn on. 
  In both cases, a small LED on the `HUT` near the charger port will turn green, indicating incoming power.


(howto-db21-shutdown)=
## How to power off a `DB21`

```{warning}
The proper shutdown protocol for a `DB21` requires having the Duckiebattery software version `2.0.0` or newer. 
To check the version of your battery, follow the instruction to "Verify current battery version" on 
[How to update a Duckiebattery](howto-db21-battery-update).
```

Make sure the Duckiebot has completed the booting process. You can verify this by checking the "Status" 
after running `dts fleet discover` on your laptop: a green `Ready` message will indicate that the Duckiebot 
has completed the booting process.

There are three methods to power off a `DB21`:

1. Using the **top** button (**preferred**):
    1. Press the **top** button (not the battery button) for 5 seconds and release;
    1. What to expect:
        1. The top button will blink for 3 seconds;
        1. The Duckiebot front and back LEDs turn off;
        1. In about *10* seconds, the on-board computer and the fan will shut down;
    1. **Troubleshooting:** If the display just switched to the next page and the top button did not blink, 
       try again and push harder on the top button during the 5 seconds;
1. Using `dts`:
    1. `dts duckiebot shutdown ![ROBOT_NAME]`
    2. What to expect:
        1. In about *10* seconds, the on-board computer and the fan will shut down;
        1. If the charging cable is not attached, the front and back LEDs will also turn off;
1. Through the Duckiebot dashboard:
    1. Open a browser
    1. Navigate to `http://![ROBOT_NAME].local`
    1. In the Top-Right corner, click on the `Power` options, and choose "`Shutdown`". Then confirm the action.
    2. What to expect:
       1. In about *10* seconds, the on-board computer and the fan will shut down;
       1. If the charging cable is not attached, the front and back LEDs will also turn off;


```{warning}
The following "hard" power shutdown should be only be used if the three methods above failed to shut down 
the Duckiebot, as it might lead to software corruption.
```

As a last resort, one could still perform a "hard" power shutdown of the `DB21`:
- `ssh duckie@![ROBOT_NAME].local sudo poweroff`;
- Unplugging the microUSB cable from the port marked as `5Vraspi` on the `HUT`;


(howto-db21m-poweron)=
## How to power on a `DB21`

To power on a `DB21` robot, press the button on the battery _once_.

The Duckiebot LEDs, as well as the on-board computer LED will turn on.

After a few seconds, the Wi-Fi dongle will start blinking. 
The Duckiebot LEDs will then turn to a steady white color, followed by the button and screen on the top 
plate powering on, as shown in the tutorial video above.

```{todo}
Replace "tutorial video above" with a proper reference once we have the video directive working.
```

(setup-duckiebot-ssh)=
## How to SSH to the Duckiebot

Next, let us try and log in onto our robot using the SSH (Secure Shell) protocol. We can do
so by running the command,

    ssh duckie@HOSTNAME.local

The default password is `quackquack`.

(howto-battery-update-pointer)=
## How to update a Duckiebattery

Follow the instructions on [how to update a Duckiebattery](howto-db21-battery-update).


(howto-hut-update)=
## How to update a `HUT`

Follow the instructions on [how to update a Duckiebot HUT](reflash-microcontroller).

```{note}
Reflashing a `HUT` is rarely needed. A notable exception is for `HUT` version 3.15 which comes with 
`DB21`s. The `HUT` version can be read on the board itself. 
```



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