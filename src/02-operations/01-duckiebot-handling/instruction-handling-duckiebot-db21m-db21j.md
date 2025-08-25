(how-to-handle-a-duckiebot-db21)=
# Duckiebot Handling (`DB21`)

```{seo}
:description: A compendium of common operations for interacting with a Duckiebot.
:keywords: Duckietown, Duckiebot, Duckiebot handling, ssh, moving a Duckiebot, Duckiebot image streaming, Duckiebot LED control, Duckiebot HUT update, Duckiebot battery update, Duckiebot remote control, Duckiebot software update
```

This chapter describes how to handle your Duckiebot.

```{needget}
- A connected Duckiebot: [](setup-duckiebot-network)
---
- 
```

(handling-tutorial-video)=
## Tutorial video

```{vimeo} 527038785
:alt: how to handle a Duckiebot DB21J
```

(handling-how-to-ssh-into-your-duckiebot)=
## How to update the software on a Duckiebot

To update the software on your Duckiebot, 



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
