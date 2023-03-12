(burn-sd-card-gui)=
# Burn the SD card - GUI

(burn-sd-card-gui-instructions)=
## Step-by-Step Instructions

Plug the SD card in your computer using an SD card reader. 
If your computer does not have one, you will find a USB to microSD card adapter in your Duckiebot kit.

Initialize the SD card by running the following command,

    dts init_sd_card --gui

A new window similar to the one shown below will pop up,

```{image} ../../_images/init-sd-card-gui-01.png
:align: center
```

Fill in the fields according to the Duckiebot you are initialization, the SD card you are using,
and the WiFi network details.

```{note}
If you need to configure **EAP (Extensible Authentication Protocol) protected networks**,
use the CLI version of the SD card flashing procedure described in [](burn-sd-card).
```

```{warning}
Given the danger of choosing a wrong device to flash (which can result in data loss and corruption of 
the Operating System), it is necessary to specify the size of the SD card you are using, so that the
program will only show you options that are compatible with your input.
```

Once you completed the form, click on the **Confirm** button to return to the terminal and confirm
the device to be flashed. When prompted, type in or copy-paste the device name from the list and 
press <kbd>Enter</kbd>.

At this point, the SD card is being flashed.
On successful end of the procedure, the drives will be automatically ejected and you will be instructed
to remove the SD card from the SD card reader and insert it into the Duckiebot's SD card slot.

If you experience any issues while flashing the SD card, make sure you check
the [](sd-card-flashing-troubleshooting) section before asking for help on Stack Overflow.
