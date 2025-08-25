(db-troubleshooting-faqs)=
# Frequently Asked Questions (FAQs)

```{seo}
:description: FAQ (Frequently Asked Questions) related to a Duckiebot.
:keywords: Duckietown, Duckiebot, FAQ, Frequently Asked Questions
```

This chapter describes frequently asked questions (FAQs) related to your Duckiebot.

```{needget}
Nothing.
---
Knowledge on FAQ related to your Duckiebot.
```

## Introduction

This chapter collects common roadblocks you may run into with your Duckiebot.
Each symptom and resolution are also available on the pages they relate to throughout the manual, so be sure to watch for troubleshooting sections and carefully complete checkpoints as you progress.

```{attention}
If you do not find a solution to your problem in this chapter:

1. Search the [Duckietown Stack Overflow](https://stackoverflowteams.com/c/duckietown/questions).
To receive an invitation, [join the Slack community](https://duckietown.com/join-slack) and follow [these instructions](https://duckietown.slack.com/archives/CHHQJ0E0H/p1670874390660429).
2. Search the Slack community `#help` channels.
3. Post your own question following the [Duckietown technical support guidelines](https://duckietown.com/contact/#technical-support).
```

(boot-faq)=
## Booting your Duckiebot

```{trouble}
My Duckiebot does not boot and when connecting it to a screen, I see only a static NVIDIA logo (occasionally flickering).
---
Follow [](db-troubleshooting-jetson-reflashing).
```

```{trouble}
I pressed the top button but my Duckiebot did not turn on.
---
Press the button on the Duckiebattery **once**.
The top button is only for turning your Duckiebot off.
```

```{trouble}
My Duckiebot does not appear to boot after pressing the button on the Duckiebattery (i.e., I don't see a green light on the Jetson Nano or HUT).
---
Follow [](assembly-instructions-db21j), checking each cable connection.
Confirm the start and end port of each power cable from the Duckiebattery.
The Duckiebattery must be fully charged, as shown in the first assembly step.
```

```{trouble}
My Duckiebot is receiving power and has an initialized SD card inserted correctly but it does not seem to boot (i.e., the Wi-Fi dongle does not blink).
---
Make sure that you specified the correct Duckiebot configuration when initializing the SD card.
```

```{trouble}
The Duckiebot screen does not turn on even though it shows up after running `dts fleet discover`, and the `Dashboard` is accessible.
The ToF sensor and front bumper are not detected on the `Components` page of the `Dashboard`.
---
Disconnect the ToF sensor from the front bumper and use the long cable that originally connected the front bumper to the HUT to connect the ToF sensor directly to that same HUT port, and then reboot you Duckiebot. This bypasses a known multiplexer issue on some bumpers.
```

```{trouble}
My Duckiebot appears to have booted and the screen is on but I can not see it after running `dts fleet discover`.
---
Follow [](db-troubleshooting-network).
```

```{trouble}
I am not sure whether my Duckiebot is properly initialized.
---
As long as your Duckiebot shows up after running `dts fleet discover`, it should be ready.
You can also visit the `Dashboard` to confirm that your Duckiebot is serving its status.
Generally, as long as you can access the `Dashboard`, your Duckiebot should be correctly initialized.
```

```{trouble}
I see a permissions error when trying to access the `Dashboard` (i.e., `Directory '/data/config/permissions'
cannot be written`).
---
1. Remove the SD card from the on-board computer (press it in once to release the spring and then remove it).
2. Put the SD card into your computer using the SD card adapter provided in the Duckiebox.
3. Navigate to the root directory of the SD card.
4. Run `chmod -R 777 ./data/config/permissions`.
5. Eject the drive, place the SD card back into the on-board computer and then turn your Duckiebot on.
```

(operation-faq)=
## Operating your Duckiebot

```{trouble}
The top button does not turn my Duckiebot off.
---
Press it harder for `5 s`.
If this does not work, run `dts duckiebot update DUCKIEBOT_NAME` and then run `dts duckiebot reboot DUCKIEBOT_NAME`.
If this does not work, follow [](db-troubleshooting-hut).
```

```{trouble}
My Duckiebot has a very low battery charge and is stuck in a boot cycle.
---
Unplug all cables connected to the HUT except minus the charging cable.
Allow the battery to charge for at least `5 h` before plugging these cables back in.
```

```{trouble}
The `Keyboard Controller` window is active but my Duckiebot still does not move. However, I can see messages being sent to my Duckiebot when looking at the `DUCKIEBOT_NAME/actuator/wheels/base/pwm` `DTPS` topic, after following [](sw-tools-dtps), and the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components`) shows a red alert for the HUT.
---
If you have a HUT v3.1, follow [](db-troubleshooting-hut).
```

```{trouble}
I have re-flashed the HUT but my Duckiebot still does not move or moves in a jerky manner. Additionally, the ToF sensor and front bumper are not detected on the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components`). I may also be having issues with the screen.
---
Disconnect the ToF sensor from the front bumper and use the long I2C cable, that originally connected the front bumper to the HUT, to connect the ToF sensor directly to that same HUT port. Finally, reboot your Duckiebot. This procedure bypasses a known multiplexer issue on some front bumpers that can cause other issues with the HUT.
```

```{trouble}
I am still having a software issue that the Duckietown team has pushed a new fix for according to Stack Overflow.
---
You can pull the latest images onto your Duckiebot by running `dts duckiebot update DUCKIEBOT_NAME`.
This is the preferred way to reset your Duckiebot's containers.
You will never need to re-flash the SD card for your Duckiebot to receive updates.
```

```{trouble}
Many of the hardware components on the `Components` page of the Dashboard are not found on my Duckiebot and their connector buses are all I2C (see the bottom line of each component card).
---
* Make sure that both rows of GPIO pins on the Jetson Nano are connected accordingly to the connection slots on the HUT.
* A broken component along the I2C bus could lead to this problem.
You could turn your Duckiebot off, unplug one element from the HUT at a time and then reboot your Duckiebot, repeat this procedure for other components.
If most missing components appear connected after one test, it is likely the unplugged component that has a hardware failure. Record a video of these tests being run and contact support.
* If all individual component unplugging tests were performed and the components along the I2C chain are still missing, there may be a I2C issue with the Jetson Nano.
From your Duckiebot, run `sudo i2cdetect -r -y 1` to see a table of I2C addresses identified and note the output. Record a video of these tests being run and contact support.
```
