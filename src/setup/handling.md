# Handling

```{seo}
:description: How to handle a Duckiebot.
:keywords: Duckietown, Duckiebot, handle
```

This chapter describes how to handle your Duckiebot.

```{needget}
Completed [](assembly/db21j.md).
---
Knowledge on how to handle your Duckiebot.
```

(handling-tutorial-video)=
## Tutorial video

```{vimeo} 527038785
```

(how-to-charge-the-Duckiebattery)=
## How to charge the Duckiebattery

To charge the Duckiebattery:

1. Plug one end of the charging cable into the `OUT` `CHARGER` port on the HUT.
2. Plug the other end of the charging cable into a `5V` `2A` power source.

```{note}
To minimize mechanical stress on the HUT, do not unplug the charging cable from the HUT.
```

```{note}
The Duckiebattery can draw up to `2A` but feeding a higher amperage will not be a problem. However, the wrong voltage can send the battery into [protection mode](db-opmanual-dtbattery-v2-protection-mode).
```

```{note}
If your Duckiebot is turned on while charging, a battery charge indicator will appear on the top right of the screen. If your Duckiebot is turned off, the LEDs will turn on. In both cases, a small LED on the HUT near the charging port will turn green, indicating incoming power.
```

(handling-how-to-turn-your-duckiebot-on)=
## How to turn your Duckiebot on

```{warning}
Make sure that your Duckiebattery is fully charged before attempting to turn your Duckiebot on.
The external power supply may not be able to provide sufficient current if the battery is low, causing the on-board computer to reboot.
Should that happen during the first boot, you will likely have to re-initialize the SD card.
```

To turn your Duckiebot on, press the button on the Duckiebattery **once**.

What to expect:

1. The front and back LEDs will turn blue, the LEDs on the on-board computer and HUT will turn on, and the fan will turn on.
2. The Wi-Fi dongle will start blinking.
3. The front and back LEDs will turn white and red, respectively.
4. The top button and screen will turn on, as shown in [](handling-tutorial-video).

To verify that your Duckiebot has completed the booting process, run the following command and wait for `Status` to change from `Booting` to `Ready`:

```shell
dts fleet discover
```

```{figure} ../_images/setup/handling/fleet_discover.png
Output of `dts fleet discover`.
```

(handling-how-to-ssh-into-your-duckiebot)=
## How to SSH into your Duckiebot

To `ssh` into your Duckiebot, using the `SSH` (`Secure Shell`) protocol, run the following command and enter the password (the default password is `quackquack`):

```shell
ssh duckie@DUCKIEBOT_NAME.local
```

(handling-how-to-turn-your-duckiebot-off)=
## How to turn your Duckiebot off

````{warning}
Run the following command and verify that `version` is greater than or equal to `2.0.2`:

```shell
dts duckiebot battery check_firmware DUCKIEBOT_NAME
```

Otherwise, follow [](duckiebattery-update) before proceeding.
````

To turn your Duckiebot off using the **top** button (**preferred**), press the **top** button (not the button on the Duckiebattery) for `5 s`.

```{attention}
If the screen switched to the next page and the top button did not blink, try again and press the **top** button harder this time.
```

To turn your Duckiebot off using `dts`, run:

```shell
dts duckiebot shutdown DUCKIEBOT_NAME
```

To turn your Duckiebot off through the `Dashboard`, after following [](../software_tools/dashboard.md):

1. Run `dts duckiebot dashboard DUCKIEBOT_NAME`.
2. Click the `Power` button.
3. Select the `Shutdown` option.
4. Click the `Yes` button.

To turn your Duckiebot off using `ssh` (**second last resort**), run:

```shell
ssh duckie@DUCKIEBOT_NAME.local sudo poweroff
```

If none of the previous methods worked, after waiting a few seconds, unplug the cable connected to the `5VRASPI` port on the HUT (**last resort**).

## How to update your Duckiebot

To update your Duckiebot, run:

```shell
dts duckiebot update DUCKIEBOT_NAME
```

## How to see what your Duckiebot sees

To see what your Duckiebot sees, follow [](../software_tools/image-viewer.md).

## How to make your Duckiebot move

To make your Duckiebot move, follow [](../software_tools/keyboard-controller.md).

## How to control your Duckiebot's LEDs

To control your Duckiebot's LEDs, follow [](../software_tools/led-controller.md).

## How to update the Duckiebattery

To update the Duckiebattery, follow [](duckiebattery-update).

## How to update the HUT

To update the HUT, follow [](../troubleshooting/hut.md).

## How to connect to your Duckiebot over the Internet

To connect to your Duckiebot over the Internet, follow [](../further_reading/zerotier.md).

## Troubleshooting

```{trouble}
I have pressed the top button down as far as it will go for `5 s` but it does not turn my Duckiebot off.
---
Run:

    `dts duckiebot update DUCKIEBOT_NAME`

    `dts duckiebot reboot DUCKIEBOT_NAME`
```

```{trouble}
I have updated and rebooted my Duckiebot but the top button still does not turn it off.
---
Update the HUT.
```

```{trouble}
My Duckiebot is stuck in a boot cycle and the Duckiebattery has a very low charge.
---
Unplug the cables connected to the `5VRASPI` and `5VEXT` ports on the HUT, and allow the Duckiebattery to charge for at least `5 h` before plugging them back in.
```
