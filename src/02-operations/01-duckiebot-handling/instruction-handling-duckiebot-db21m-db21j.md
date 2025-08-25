(how-to-handle-a-duckiebot-db21)=
# Duckiebot Handling Cheatsheet (`DB21`)

```{seo}
:description: A compendium of common operations for interacting with a Duckiebot.
:keywords: Duckietown, Duckiebot, Duckiebot handling, ssh, moving a Duckiebot, Duckiebot image streaming, Duckiebot LED control, Duckiebot HUT update, Duckiebot battery update, Duckiebot remote control, Duckiebot software update
```

This chapter describes how to handle your Duckiebot.

```{needget}
- A connected Duckiebot: [](setup-duckiebot-network)
---
- A "cheatsheet" for common Duckiebot operations
```


(handling-how-to-update-db-software)=
## How to update the software on a Duckiebot

To update the software on your Duckiebot, run:

```shell
dts duckiebot update ROBOT_NAME
```

(handling-how-to-ssh-into-your-duckiebot)=
## How to SSH into your Duckiebot

To `ssh` into your Duckiebot, using the `SSH` (`Secure Shell`) protocol, run the following command and enter the password (the default password is `quackquack`):

```shell
ssh duckie@DUCKIEBOT_NAME.local
```

## How to see what your Duckiebot sees

To see what your Duckiebot sees, follow [](ops-db-subsys-make-it-see).

## How to make your Duckiebot move

To make your Duckiebot move, follow [](ops-db-subsys-make-it-move).

## How to control your Duckiebot's LEDs

To control your Duckiebot's LEDs, follow [](ops-db-subsys-make-it-shine).

## How to update the Duckiebattery

To update the Duckiebattery, follow [](duckiebattery-update).

### How to check the charging efficiency of your Duckiebot

Once your Duckiebattery is up to date and your Duckiebot is connected, run:

    dts duckiebot battery info ROBOT_NAME

```shell
battery:
  cell_voltage: 3.59
  charging: true
  current: 0.84
  cycle_count: 20
  input_voltage: 4.82
  percentage: 12
  present: true
  temperature: 39.85
  time_to_empty: 3932100
  usb_out_1_voltage: 4.73
  usb_out_2_voltage: 5.01
```

## How to update the HUT

To update the HUT, follow [](reflash-microcontroller).

## How to connect to your Duckiebot over the Internet

To connect to your Duckiebot over the Internet, follow [](protip-zerotier-remote-duckiebot-control).

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
