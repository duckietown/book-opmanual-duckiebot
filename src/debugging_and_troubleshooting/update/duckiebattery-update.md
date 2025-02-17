```{seo}
:description: How to update a Duckiebattery
:keywords: Duckietown, Duckiebot, battery, update
```

(howto-db21-battery-update)=
# Debug - Updating a Duckiebattery

To update the software running on the microcontroller in the Duckiebattery, or just to check its current version, use the following instructions.

```{note}
These instructions work for [the Duckiebattery](db-opmanual-dtbattery-v2). Make sure you have the correct version before proceeding. 
```

***Important:***

1. Before the battery upgrade, please make sure the battery has at least 15% of charge.
2. Run all the following commands on the desktop/laptop

Make sure the Duckiebot is powered on and connected to the network. 
You can verify the latter by launching, e.g., `dts fleet discover` and finding that your Duckiebot is on the list.

1. Please update the `duckietown-shell` utility:
    1. `pip3 install --user --upgrade --no-cache-dir duckietown-shell`
    2. `dts update`
    3. `dts desktop update`
2. Update the Duckiebot:
    1. `dts duckiebot update ![ROBOT_NAME]`
3. Reboot the Duckiebot:
    1. `ssh duckie@![ROBOT_NAME].local sudo reboot`
    2. Wait until the Duckiebot reboots and the display shows information (especially about the battery).
    3. You could verify the battery related software is up and running by checking  whether the display reacts correctly to charging states when a charging cable is plugged in and unplugged.
4. Upgrade the battery firmware:
    1. `dts duckiebot battery upgrade ![ROBOT_NAME]`
        1. Note: When prompted to "double-click" on the battery button, make sure to _quickly_ click twice the _battery_ button.
        2. Note: Do not worry if you are unsure if you actually pressed the button twice or not, as the battery upgrade process will verify this.
        3. Follow the instructions in the terminal.
    2. If the command finished with the error: ```SAM-BA operation failed INFO:UpgradeHelper:An error occurred while flashing the battery. ERROR:dts:The battery reported the status 'GENERIC_ERROR'```, please try flashing again with: `dts duckiebot battery upgrade --force ![ROBOT_NAME]`
    3. If the command finished with any other error: **single** press the battery button, and start from _step 3_ again one more time. If there are still errors, please report on StackOverflow.
5. Prepare for post-upgrade checks
    1. If the battery indicates the charging states correctly, and shows the percentage number normally, proceed to _step 6_
    2. If the display shows "`NoBT`" (No battery detected), then **single** press the battery button, and run:
        1. `ssh duckie@![ROBOT_NAME].local sudo reboot`
        2. Wait for the reboot (as described in _step 3_)
        3. Then proceed to _step 6_
6. Verify current battery version:
    1. Method 1:
        1. `dts duckiebot battery check_firmware ![ROBOT_NAME]`
        2. Verify the battery version should be `2.0.2` or newer
    2. Method 2:
        1. Open a browser window
        2. Navigate to `http://![ROBOT_NAME].local/health/battery/info`
        3. Verify the battery version should be `2.0.2` or newer