(troubleshooting-faq)=
# Duckiebot FAQ Guide

This FAQ page collects common roadblocks you might run into when setting up your Duckietown environment and 
operating your Duckiebot.

Each symptom and resolution are also available on the pages they relate to throughout the manual along with more 
detailed troubleshooting on that topic.

If you don't find the solutions you need in this book, be sure to first search the Duckietown Stack 
Overflow and Slack for previous answers, then post your own question following the support guidelines on Slack.

(install-faq)=
## FAQs: Installing the Duckietown Tools

(boot-faq)=
## FAQs: Booting your Duckiebot

```{trouble}
I pressed the power button on top but nothing happened.
---
Power on your Duckiebot using the button on the side of the Duckiebattery.  The top button is only for powering off. 
 You can also learn more about how to handle your Duckiebot in [](handling-duckiebot-db21).
```

```{trouble}
My Duckiebot does not appear to boot after pressing the power button on the battery. I don't see a green light on 
the HUT or the Jetson Nano.
---
Refer back to [](assembling-duckiebot-db21j), and check each of your cable connections.  Confirm the start and end 
port of each power cable from the battery.  The battery must be charged fully as shown in the first assembly step.
```

```{trouble}
My Duckiebot is getting power but does not appear to be booting. The Wifi dongle is not blinking.
---
Make sure you flashed the SD card following the instructions in [](setup-duckiebot-sd-card).
```

```{trouble}
My Duckiebot is getting power but does not appear to be booting. The Wifi dongle is not blinking.
---
Make sure that you correctly specified the model of your Duckiebot when initializing the SD card.

If you have a Duckiebot with a 2GB Jetson Nano - the model is DB21M

If you have a Duckiebot with a 4GB Jetson Nano - the model is DB21J

If you are not using a Jetson Nano, the model is the model of your Duckiebot (ex. DB19 or DBR4)
```

```{trouble}
My Duckiebot appears to be booted and the screen is on, but I can't see it using `dts fleet discover`.
---
Your Duckiebot must be connected to the same network as the computer you are using to run the `dts` commands.  Check 
the [networking section](duckiebot-network) of the book to see if your network is set up correctly.
```

```{trouble}
I am not sure whether my Duckiebot is properly initialized.
---
As long as the `fleet discover` tool shows ready, your Duckiebot should be ready. 
You can also visit the dashboard to confirm that the Duckiebot is serving its status. 
Generally as long as you see the Duckiebot dashboard is up, your Duckiebot should be correctly initialized.
```

(operation-faq)=
## FAQs: Operating your Duckiebot

```{trouble}
My Duckiebot does not drive when I use the keyboard control GUI.
---

```

```{trouble}

---

```
