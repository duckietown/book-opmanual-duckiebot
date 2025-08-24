(ops-db-battery-update)=
# Debug - Duckiebattery Software Update

```{seo}
:description: Learn how to update the software on your Duckiebattery, a smart battery for autonomous robotics applications. 
:keywords: duckiebattery update, duckiebattery software update, duckiebot battery update
```

```{needget}
- A correctly assembled Duckiebot
- Battery with at 15 percent residual charge
---
- An up to date Duckiebattery
```

The Duckiebattery is a programmable smart battery, custom designed for autonomous robotics applications. 

(duckiebattery-update)=
## Duckiebattery software update

To update the Duckiebattery:

1. Run `pipx upgrade duckietown-shell`.
2. Run `dts update`.
3. Run `dts desktop update`.
4. Run `dts fleet discover` and verify that your Duckiebot is `Ready`.
5. Run `dts duckiebot update DUCKIEBOT_NAME`.
6. Run `dts duckiebot battery info DUCKIEBOT_NAME` and verify that `percentage` is greater than `15`.
7. Run `dts duckiebot battery upgrade DUCKIEBOT_NAME` and follow the instructions. If prompted to "double-click" the Duckiebattery's button, *quickly* press the Duckiebattery's button **twice**.
8. (optional) If the display shows "NoBT", press the Duckiebattery's button **once** and reboot your Duckiebot.
9. Run `dts duckiebot battery check_firmware DUCKIEBOT_NAME` and verify that `version` is greater than or equal to `2.0.2`.

````{attention}
If the output of step 7 is `SAM-BA operation failed INFO:UpgradeHelper:An error occurred while flashing the battery. ERROR:dts:The battery reported the status 'GENERIC_ERROR'`, run:

```shell
dts duckiebot battery upgrade --force DUCKIEBOT_NAME
```

Otherwise, if the output of the step 7 is any other error message, press the Duckiebattery's button **once**, reboot your Duckiebot and try again.
````

## Checkpoint!

To make sure the installation was completed successfully:

```{testexpect}
Look at the Duckiebot screen, and plug in and out the charger.
---
You should see the screen react to the different charging states.
```

```{testexpect}
Perform one of the [Duckiebot soft shutdown procedures](duckiebot-soft-shutdown).
---
The Duckiebot shuts down successfully.
```