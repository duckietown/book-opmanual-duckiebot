```{seo}
:description: How to handle a Duckiebot `DB21`
:keywords: Duckietown, Duckiebot, handle
```

(handling-duckiebot-db21)=
# Handling - Duckiebot DB21

This section describes how to handle your Duckiebot `DB21` (`DB21M`/`DB21J`).

```{needget}
* An assembled Duckiebot `DB21`.
* An initialized Duckiebot `DB21` with **firmware version 1.2.2 or newer**. Check your Duckiebot's firmware version by following [](duckiebot-dashboard-use) before proceeding.
---
Knowledge on how to handle your Duckiebot `DB21`.
```

```{attention}
For all **Handling**, **Operation** and **Calibration** commands that use your Duckiebot's name, replace `![DUCKIEBOT_NAME]` with your Duckiebot's `hostname`, which does not include `.local` at the end.
```

(tutorial-handling-db21-video)=
## Tutorial video

```{vimeo} 527038785
```

(howto-db21-charge)=
## How to charge the Duckiebattery

To charge the Duckiebattery:
1. Plug one end of the charging cable into the `OUT` `CHARGER` port on the HUT
2. Plug the other end of the charging cable into a `5V` `2A` power source

```{note}
To minimize mechanical stress on the HUT, do not unplug the charging cable from the HUT.
```

```{note}
The Duckiebattery can draw up to `2A` but feeding a higher amperage will not be a problem. However, the wrong voltage can send the battery into [protection mode](db-opmanual-dtbattery-v2-protection-mode).
```

```{note}
If your Duckiebot is turned on while charging, a battery charge indicator will appear on the top right of the screen. If your Duckiebot is turned off, the LEDs will turn on. In both cases, a small LED on the HUT near the charging port will turn green, indicating incoming power.
```

(howto-db21-poweron)=
## How to turn your Duckiebot on

To turn your Duckiebot on, press the button on the Duckiebattery **once**.

What to expect:
1. The front and back LEDs will turn blue, the LEDs on the on-board computer and HUT will turn on, and the fan will turn on
2. The Wi-Fi dongle will start blinking
3. The front and back LEDs will turn white and red, respectively
4. The top button and screen will turn on, as shown in [](tutorial-handling-db21-video)

(setup-duckiebot-ssh)=
## How to SSH into your Duckiebot

To `ssh` into your Duckiebot, using the `SSH` (`Secure Shell`) protocol, run the following command and enter the password (the default password is `quackquack`):

    ssh duckie@![DUCKIEBOT_NAME].local

(howto-db21-shutdown)=
## How to turn your Duckiebot off

```{warning}
The proper shutdown protocol for a Duckiebot `DB21` requires the **Duckiebattery software version 2.0.0 or newer**. Check your Duckiebot's Duckiebattery software version by following [](howto-db21-battery-update) before proceeding.
```

To verify that your Duckiebot has completed the booting process, run the following command and check that `Status` is set to `Ready`:

    dts fleet discover

To turn your Duckiebot off using the **top** button (**preferred**), press the **top** button (not the button on the Duckiebattery) for **5** seconds.

```{attention}
If the screen switched to the next page and the top button did not blink, try again and press the **top** button harder this time.
```

To turn your Duckiebot off using `dts`, run:

    dts duckiebot shutdown ![DUCKIEBOT_NAME]

To turn your Duckiebot off through the `Dashboard`:
1. Run `dts duckiebot dashboard ![DUCKIEBOT_NAME]`
2. Click the `Power` button
3. Select the `Shutdown` option
4. Click the `Yes` button

To turn your Duckiebot off using `ssh` (**second last resort**), run:

    ssh duckie@![DUCKIEBOT_NAME].local sudo poweroff

If none of the previous methods worked, after waiting a few seconds, unplug the cable connected to the `5VRASPI` port on the HUT (**last resort**).

(howto-battery-update-pointer)=
## How to update the Duckiebattery

To update the Duckiebattery, follow [](howto-db21-battery-update).

(howto-hut-update)=
## How to update the HUT

To update the HUT, follow [](reflash-microcontroller).

## Troubleshooting

```{trouble}
I have pressed the top button down as far as it will go for 5 seconds but it does not turn my Duckiebot off.
---
Run:

    `dts duckiebot update ![DUCKIEBOT_NAME]`

    `dts duckiebot reboot ![DUCKIEBOT_NAME]`
```

```{trouble}
I have updated and rebooted my Duckiebot but the top button still does not turn it off.
---
Re-flash the HUT.
```

```{trouble}
My Duckiebot is stuck in a boot cycle and the Duckiebattery has a very low charge.
---
Unplug the cables connected to the `5VRASPI` and `5VEXT` ports on the HUT, and allow the Duckiebattery to charge for at least 5 hours before plugging them back in.
```
