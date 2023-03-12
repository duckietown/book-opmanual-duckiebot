# Troubleshooting

(sd-card-flashing-troubleshooting)=
## Troubleshoot - SD card flashing

```{trouble}
- The SD card doesn't seem to be written.
- The flashing process seemed too fast, there is no data on my SD card.
---
- Check if your SD card has a write protection switch.
- Make sure you inputted the correct drive name during the flashing procedure.
```


```{trouble}
The flashing procedure fails with a `Bad archive` error.
---
This happens when the downloaded compressed disk image file appears corrupted. You can force the re-download by adding the option `--no-cache` to the `init_sd_card` command.
```

```{trouble}
The verification process fails with error `Please set up a token using "dts tok set"`.
---
Make sure you completed the Duckietown token setup procedure [](#dt-account).
```

(duckiebot-first-boot-troubleshooting)=
## Troubleshoot - First Boot

```{trouble}
The red LED on the Raspberry Pi is OFF.
---
Press the button on the side of the battery ([](troubleshooting-battery-button)).
```

```{trouble}
The Raspberry Pi has power but it does not boot.
---
[Initialize the SD card](setup-duckiebot) if not done already. If problem persists, ask on 
[Stack Overflow](https://stackoverflowteams.com/c/duckietown).
```


```{trouble}
I cannot ping the Duckiebot.
---
Check the [networking section](duckiebot-network) of the book to see if your network is set up correctly.
```


```{trouble}
I am not sure whether the Duckiebot is properly initialized.
---
As long as the fleet discover tool shows ready, your Duckiebot should be ready. 
You can also visit `http://HOSTNAME.local/docker/` to see all the container status. 
Generally as long as you see the Duckiebot web UI is up, your Duckiebot should be correctly initialized.
```


```{trouble}
**`DB18` and `DB19` only**: The LEDs light up in a variety of colors when the battery is plugged in for the first time.
---
The LEDs of the (`DB18` and `DB19`) Duckiebot should light up in white as soon as you power the Duckiebot. 
If the LEDs turn on and shine in any different color than white, probably the code on the microcontroller 
is corrupted. You can reflash it using the procedure in [](#reflash-microcontroller).
```


```{trouble}
On first boot, the lights of the Duckiebot do not turn white (might be blue).
---
Run the following commands `dts duckiebot update HOSTNAME`      
```

