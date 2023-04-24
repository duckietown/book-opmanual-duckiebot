(burn-sd-card)=
# Burn the SD card - CLI

```{attention}
Please note: You will need to specify the model of your Duckiebot when initializing the SD card.

* If you have a Duckiebot with a **2GB** Jetson Nano - the model is **DB21M**
* If you have a Duckiebot with a **4GB** Jetson Nano - the model is **DB21J**
* If you are not using a Jetson Nano, the model is the model of your Duckiebot (ex. DB19 or DBR4)
```

(burn-sd-card-video)=
## Video Tutorial 

```{vimeo} 526698325
```


(burn-sd-card-instructions)=
## Step-by-Step Instructions

Plug the SD card in your computer using an SD card reader. 
If your computer does not have one, you will find a USB to microSD card adapter in your Duckiebot kit.

Initialize the SD card by running the following command,

    dts init_sd_card --hostname HOSTNAME --type TYPE --configuration CONFIGURATION --wifi WIFI

where,

    --hostname          Name of the robot to flash the SD card for.
    --type              The type of your device. Types are `duckiebot` (default),
                        `watchtower`, `traffic_light`.
    --configuration     The model of your robot. This is associated with
                        `--type` option. E.g. `DB21J`, `DB21M`, `DB19`, or `DB18`.


Other options are:

    --wifi              A comma-separated list of WiFi networks, aeach network is passed in the format ![wifi_name]:![wifi_password]
                        default: duckietown:quackquack
    --country           Country code.
                        default: US

```{note}
The default username and password are `duckie` and `quackquack`, respectively.
```

If you plan on connecting with the Duckiebot over different networks (e.g., at home and in class), 
you can list all your networks like in the following example,

    dts init_sd_card ... --wifi duckietown:quackquack,myhomenetwork:myhomepassword,myuninetwork:myunipassword

```{note}
There should be no space after the commas.
```

Watchtowers and traffic lights by default have Wi-Fi not configured, 
as we recommend hard wiring them with Ethernet cables. 
Default Wi-Fi settings for other robot types is `duckietown:quackquack`.

Each network defined in the list can support the following arguments:

      - Open networks (no password): "ssid"
      - PSK (Pre-shared key) protected networks: "ssid:psk"
      - EAP (Extensible Authentication Protocol) protected networks: "ssid:username:password"

Make sure to set your country correctly with the `--country` option 
(e.g., CA for Canada, CH for Switzerland, US for the United States of America). 
Neglecting this sometimes will result in specific Wi-Fi hot-spots not being seen by the Duckiebot.

Additional options for `init_sd_card` exist. For a full list of the options, run:

    dts init_sd_card --help

After you run the `dts init_sd_card` command, follow the instructions that appear on screen.

Part of this procedure includes accepting the Duckietown Software License, Terms and Conditions
and Privacy Policy, as well as robot configuration-specific licenses due to the presence of third
party software in the SD card.

The next step is that of choosing among all the devices connected to your computer, which one
represents the SD card that you want to flash for your Duckiebot. Given the danger of choosing a
wrong device (from data loss to OS files corruption), the program will guide you through this step
by asking the size of the SD card. Devices that do not match the given size will not be shown.

Type in or copy-paste the device name from the list and press <kbd>Enter</kbd>.

At this point, the SD card is being flashed.
On successful end of the procedure, the drives will be automatically ejected and you will be instructed
to remove the SD card from the SD card reader and insert it into the Duckiebot's SD card slot.

If you experience any issues while flashing the SD card, make sure you check 
the [](sd-card-flashing-troubleshooting) section before asking for help on Stack Overflow.

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
